# Supabase Setup Guide - Women's Health Tracker

## Project Setup

### 1. Create New Project
1. Go to [supabase.com](https://supabase.com) and create new project
2. Choose a project name: `womens-health-tracker-dev`
3. Generate a strong database password (save it!)
4. Select your preferred region
5. Wait for project initialization (~2 minutes)

### 2. Database Schema Creation

Navigate to **SQL Editor** in your Supabase dashboard and run these commands in order:

#### Step 1: Enable Extensions
```sql
-- Enable UUID extension for generating unique IDs
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

-- Note: RLS is enabled by default in Supabase, no need to set JWT secret manually
```

#### Step 2: Create Menstrual Cycles Table (Simplified)
```sql
CREATE TABLE menstrual_cycles (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    start_date DATE NOT NULL,
    end_date DATE,
    cycle_length INTEGER,
    is_current BOOLEAN DEFAULT false,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    
    -- Ensure only one current cycle total (single user)
    CONSTRAINT unique_current_cycle EXCLUDE (is_current WITH =) WHERE (is_current = true)
);

-- No RLS needed for single user
-- Indexes for better performance
CREATE INDEX idx_cycles_start_date ON menstrual_cycles(start_date);
CREATE INDEX idx_cycles_current ON menstrual_cycles(is_current) WHERE is_current = true;
```

#### Step 3: Create Daily Entries Table (Simplified)
```sql
CREATE TABLE daily_entries (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    cycle_id UUID REFERENCES menstrual_cycles(id) ON DELETE SET NULL,
    entry_date DATE NOT NULL,
    cycle_day INTEGER,
    
    -- Health metrics (1-5 scale)
    muscle_pain INTEGER CHECK (muscle_pain >= 1 AND muscle_pain <= 5),
    joint_pain INTEGER CHECK (joint_pain >= 1 AND joint_pain <= 5),
    headache INTEGER CHECK (headache >= 1 AND headache <= 5),
    energy_level INTEGER CHECK (energy_level >= 1 AND energy_level <= 5),
    sleep_quality INTEGER CHECK (sleep_quality >= 1 AND sleep_quality <= 5),
    mood INTEGER CHECK (mood >= 1 AND mood <= 5),
    
    -- Period tracking
    period_flow VARCHAR(20) CHECK (period_flow IN ('none', 'spotting', 'light', 'medium', 'heavy')),
    period_symptoms TEXT[], -- Array of symptoms like ['cramps', 'bloating']
    
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    
    -- Unique constraint: one entry per date (single user)
    CONSTRAINT unique_entry_date UNIQUE (entry_date)
);

-- No RLS needed for single user
-- Indexes
CREATE INDEX idx_entries_date ON daily_entries(entry_date);
CREATE INDEX idx_entries_cycle_id ON daily_entries(cycle_id);
CREATE INDEX idx_entries_recent ON daily_entries(entry_date) WHERE entry_date >= CURRENT_DATE - INTERVAL '90 days';
```

#### Step 4: Create Helper Functions (Simplified)
```sql
-- Function to calculate cycle day (simplified for single user)
CREATE OR REPLACE FUNCTION calculate_cycle_day(entry_date DATE)
RETURNS INTEGER AS $
DECLARE
    cycle_start DATE;
    cycle_day_result INTEGER;
BEGIN
    -- Find the current cycle start date
    SELECT start_date INTO cycle_start
    FROM menstrual_cycles 
    WHERE start_date <= entry_date
    ORDER BY start_date DESC
    LIMIT 1;
    
    -- Calculate cycle day
    IF cycle_start IS NOT NULL THEN
        cycle_day_result := entry_date - cycle_start + 1;
        RETURN cycle_day_result;
    ELSE
        RETURN NULL;
    END IF;
END;
$ LANGUAGE plpgsql SECURITY DEFINER;

-- Function to auto-update cycle_day when inserting/updating daily entries
CREATE OR REPLACE FUNCTION update_cycle_day()
RETURNS TRIGGER AS $
BEGIN
    NEW.cycle_day := calculate_cycle_day(NEW.entry_date);
    NEW.updated_at := NOW();
    RETURN NEW;
END;
$ LANGUAGE plpgsql;

-- Trigger to automatically calculate cycle_day
CREATE TRIGGER trigger_update_cycle_day
    BEFORE INSERT OR UPDATE ON daily_entries
    FOR EACH ROW EXECUTE FUNCTION update_cycle_day();

-- Function to update cycle length when cycle ends
CREATE OR REPLACE FUNCTION update_cycle_length()
RETURNS TRIGGER AS $
BEGIN
    -- If end_date is being set, calculate cycle length
    IF NEW.end_date IS NOT NULL AND OLD.end_date IS NULL THEN
        NEW.cycle_length := NEW.end_date - NEW.start_date + 1;
        NEW.updated_at := NOW();
    END IF;
    RETURN NEW;
END;
$ LANGUAGE plpgsql;

-- Trigger for cycle length calculation
CREATE TRIGGER trigger_update_cycle_length
    BEFORE UPDATE ON menstrual_cycles
    FOR EACH ROW EXECUTE FUNCTION update_cycle_length();
```

## API Configuration (Simplified)

### 1. Get Your Keys
Go to **Settings > API** (or **Project Settings > API**):

- **Project URL**: `https://your-project-ref.supabase.co`
- **anon/public key**: For client-side operations (this is all you need)

**Note:** Since there's no authentication, you only need the anon key. No service_role key needed.

### 2. No RLS Setup Needed
Since this is a single-user app, Row Level Security has been skipped entirely. All data is accessible without authentication barriers.

## Database Optimization

### 1. Additional Indexes for Performance
```sql
-- Composite index for common queries
CREATE INDEX idx_entries_user_date_desc ON daily_entries(user_id, entry_date DESC);

-- Index for chart queries (last 90 days)
CREATE INDEX idx_entries_recent ON daily_entries(user_id, entry_date) 
WHERE entry_date >= CURRENT_DATE - INTERVAL '90 days';

-- Index for cycle queries
CREATE INDEX idx_cycles_user_date_desc ON menstrual_cycles(user_id, start_date DESC);
```

### 2. Enable Realtime (Optional)
If you want real-time updates:
```sql
-- Enable realtime for tables
ALTER PUBLICATION supabase_realtime ADD TABLE daily_entries;
ALTER PUBLICATION supabase_realtime ADD TABLE menstrual_cycles;
```

## Testing Your Setup

### 1. Test Data Insertion (Simplified)
```sql
-- Insert test cycle
INSERT INTO menstrual_cycles (start_date, is_current) 
VALUES ('2024-01-01', true);

-- Insert test daily entry
INSERT INTO daily_entries (entry_date, muscle_pain, energy_level, period_flow) 
VALUES ('2024-01-02', 3, 4, 'medium');

-- Verify cycle_day was calculated automatically
SELECT entry_date, cycle_day, muscle_pain, energy_level FROM daily_entries;

-- Insert a few more entries to see the pattern
INSERT INTO daily_entries (entry_date, muscle_pain, energy_level, period_flow) 
VALUES 
    ('2024-01-03', 2, 5, 'light'),
    ('2024-01-04', 1, 4, 'none'),
    ('2024-01-05', 2, 3, 'none');

-- Check all entries with cycle days
SELECT entry_date, cycle_day, muscle_pain, energy_level, period_flow 
FROM daily_entries 
ORDER BY entry_date;
```

## Security Checklist (Simplified)

### Development Settings ✅
- [x] Tables created without RLS (single user)
- [x] Foreign key constraints in place
- [x] Check constraints for data validation
- [x] Unique constraints prevent duplicate entries
- [x] No authentication complexity

### Production Checklist (for later if adding multi-user)
- [ ] Add authentication system
- [ ] Implement RLS policies
- [ ] Set up user management
- [ ] Configure proper security settings

## Connection Details for Lovable

Provide Lovable with these details:

```env
SUPABASE_URL=https://your-project-ref.supabase.co
SUPABASE_ANON_KEY=your-anon-key-here
```

**Note:** Only the anon key is needed since there's no authentication.

## Common Queries for Development (Simplified)

```sql
-- Get last 30 days of data
SELECT * FROM daily_entries 
WHERE entry_date >= CURRENT_DATE - INTERVAL '30 days'
ORDER BY entry_date DESC;

-- Get current cycle info
SELECT * FROM menstrual_cycles 
WHERE is_current = true;

-- Calculate average cycle length
SELECT AVG(cycle_length) as avg_cycle_length
FROM menstrual_cycles 
WHERE cycle_length IS NOT NULL;

-- Get all entries for current cycle
SELECT de.*, mc.start_date as cycle_start
FROM daily_entries de
LEFT JOIN menstrual_cycles mc ON de.cycle_id = mc.id
WHERE mc.is_current = true
ORDER BY de.entry_date;
```

## Adding Historical Data for Testing

### Method 1: Through the UI (Recommended)
The app should allow you to:
- Change the date at the top of the entry form
- Navigate to previous dates using arrows or date picker
- Enter data for any past date (up to 90 days back)

### Method 2: Direct Database Insertion
If you need to bulk insert historical data:

```sql
-- First, make sure you have a current cycle
INSERT INTO menstrual_cycles (start_date, is_current) 
VALUES ('2024-01-01', true);

-- Bulk insert historical entries
INSERT INTO daily_entries (entry_date, muscle_pain, joint_pain, headache, energy_level, sleep_quality, mood, period_flow) VALUES
('2024-01-01', 4, 3, 2, 3, 4, 4, 'heavy'),
('2024-01-02', 3, 2, 1, 4, 4, 4, 'medium'),
('2024-01-03', 2, 2, 1, 4, 5, 5, 'light'),
('2024-01-04', 1, 1, 1, 5, 5, 5, 'none'),
('2024-01-05', 1, 1, 1, 4, 4, 4, 'none'),
-- Add more dates as needed
('2024-01-10', 2, 2, 3, 3, 3, 3, 'none'),
('2024-01-15', 3, 3, 4, 2, 2, 2, 'none');

-- Verify the cycle_day was calculated correctly
SELECT entry_date, cycle_day, energy_level, period_flow 
FROM daily_entries 
ORDER BY entry_date;
```

### Method 3: CSV Import Script
For large amounts of test data, you could create a CSV file:

```csv
entry_date,muscle_pain,joint_pain,headache,energy_level,sleep_quality,mood,period_flow
2024-01-01,4,3,2,3,4,4,heavy
2024-01-02,3,2,1,4,4,4,medium
2024-01-03,2,2,1,4,5,5,light
```

Then import using Supabase dashboard or a script.