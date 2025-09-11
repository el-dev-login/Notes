# Women's Health Tracker - Lovable Prompt

## App Requirements

Build a web app that tracks women's health metrics for athletes with the following features:

### Core Functionality
- **Daily tracking**: muscle pain, joint pain, headaches, energy levels, sleep quality, mood (1-5 scales)
- **Period tracking**: flow intensity and cycle management
- **Data visualization**: 3-month grid view showing all metrics with color coding
- **Simple interface**: prioritize quick daily input with dropdowns/sliders
- **Black and white color scheme** with minimal design

### Key UI Requirements
- **Home screen**: Daily entry form with today's date as default
- **Quick input**: All health metrics as 1-5 sliders or dropdowns
- **Period toggle**: Simple on/off with flow selector (none, spotting, light, medium, heavy)
- **Chart view**: 3-month timeline showing all tracked data in grid format
- **Cycle info**: Display current cycle day and days since last period
- **Navigation**: Simple menu between daily entry and chart views

## Database Setup (ALREADY CONFIGURED)

**Important**: Do NOT create or modify database tables. Use the existing Supabase setup:

### Connection Details
```env
SUPABASE_URL=https://[your-project-ref].supabase.co
SUPABASE_ANON_KEY=[your-anon-key]
```

### Database Schema (Use As-Is - Simplified for Single User)
```sql
-- Menstrual cycles table
menstrual_cycles (
    id UUID PRIMARY KEY,
    start_date DATE,
    end_date DATE,
    cycle_length INTEGER,
    is_current BOOLEAN,
    created_at TIMESTAMP
)

-- Daily entries table
daily_entries (
    id UUID PRIMARY KEY,
    cycle_id UUID REFERENCES menstrual_cycles(id),
    entry_date DATE,
    cycle_day INTEGER, -- Auto-calculated by database
    
    -- Health metrics (1-5 scale)
    muscle_pain INTEGER,
    joint_pain INTEGER,
    headache INTEGER,
    energy_level INTEGER,
    sleep_quality INTEGER,
    mood INTEGER,
    
    -- Period tracking
    period_flow VARCHAR, -- 'none', 'spotting', 'light', 'medium', 'heavy'
    period_symptoms TEXT[],
    
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    
    UNIQUE(entry_date) -- One entry per date (single user)
)
```

### Database Integration Requirements (Simplified)
- Use `@supabase/supabase-js` for all database operations
- NO authentication needed - skip all auth flows
- NO Row Level Security - all data is accessible
- The `cycle_day` field is auto-calculated by database triggers
- Use the existing foreign key relationships between tables

## Technical Specifications

### Required API Operations (Simplified)
```javascript
// Daily entries - no user_id needed
const { data, error } = await supabase
  .from('daily_entries')
  .insert([{ 
    entry_date: '2024-01-15',
    muscle_pain: 3,
    energy_level: 4,
    period_flow: 'medium'
  }]);

// Get chart data (last 90 days) - no user filtering
const { data } = await supabase
  .from('daily_entries')
  .select('*')
  .gte('entry_date', date90DaysAgo)
  .order('entry_date', { ascending: false });

// Current cycle info - no user filtering
const { data } = await supabase
  .from('menstrual_cycles')
  .select('*')
  .eq('is_current', true)
  .single();
```

### Authentication Flow
- Email/password signup and login using Supabase Auth
- Redirect to profile setup after first signup
- Auto-create user record in `users` table after auth
- Protect all routes except login/signup

### Data Validation
- All health metrics: integers 1-5 only
- Period flow: enum values only ('none', 'spotting', 'light', 'medium', 'heavy')
- Entry date: cannot be future date
- One entry per user per date (database constraint handles this)

## UI/UX Specifications

### Design System & Visual Requirements

**IMPORTANT**: This app should NOT look like typical women's health apps. Avoid all pink, floral, or "feminine" design elements.

#### Color Palette (Strict)
- **Primary**: Pure black (#000000) for text and borders
- **Secondary**: Pure white (#FFFFFF) for backgrounds
- **Accents**: Grayscale only (#F8F9FA, #E9ECEF, #DEE2E6, #6C757D)
- **Data visualization**: Use grayscale gradients (light gray = low values, dark gray/black = high values)
- **Interactive elements**: Black borders, gray hover states
- **NO other colors**: Absolutely no pink, purple, pastels, or "wellness" colors

#### Typography
- **Font**: Modern sans-serif (Inter, Helvetica, or system fonts)
- **Hierarchy**: Bold weights for headers, regular for body text
- **Style**: Clean, technical, professional - think fitness tracker, not lifestyle app
- **Sizing**: Generous spacing, clear hierarchy

#### Visual Style
- **Aesthetic**: Minimalist, data-focused, almost clinical
- **Inspiration**: Think Apple Health, fitness trackers, or technical dashboards
- **Avoid**: Rounded corners everywhere, soft shadows, decorative elements
- **Embrace**: Sharp edges, clean lines, grid-based layouts, high contrast

#### Interactive Elements
- **Buttons**: Sharp rectangular buttons with black borders, white fill, black text
- **Sliders**: Clean horizontal sliders with minimal styling
- **Forms**: Clean input fields with sharp borders
- **Hover states**: Subtle gray backgrounds, never color changes
- **Focus states**: Black outlines, high contrast

### Component Styling Guidelines

#### Data Entry Interface
```
Sliders:
- Clean horizontal bars with sharp rectangular handles
- Gray track, black handle, black fill for selected portion
- Numerical values displayed prominently (large, bold numbers)
- Labels in small, uppercase text

Dropdowns:
- Sharp rectangular borders, no rounded corners
- White background, black text, black border
- Clean list items with hover states in light gray

Buttons:
- Primary: Black background, white text, sharp corners
- Secondary: White background, black text, black border
- No gradients, shadows, or decorative elements
```

#### Chart/Grid Visualization
```
Grid cells:
- Perfect squares or rectangles
- Sharp borders between cells
- Grayscale fill based on data intensity:
  * 1 (lowest): White or very light gray
  * 3 (medium): Medium gray
  * 5 (highest): Black or very dark gray
- Period days: Subtle black border or different pattern

Calendar layout:
- Clean grid structure
- Month/week headers in bold, uppercase
- Minimal spacing, maximum data density
```

#### Layout & Spacing
- **Grid system**: Strict alignment, consistent spacing
- **White space**: Generous but purposeful, not decorative
- **Hierarchy**: Size and weight differences, not color
- **Information density**: Pack information efficiently, like a dashboard

### Layout Specifications

#### Home Screen Layout
```
Header: 
- Date selector with left/right arrows: "← JAN 15, 2024 →"
- Cycle info below: "Day 15 of cycle | 3 days since period"
- If data exists for date: "UPDATING ENTRY" vs "NEW ENTRY"

Daily Entry Form:
- Period Status: Clean toggle + flow dropdown when ON
- Health Metrics: 6 horizontal sliders in a grid (2x3 or 3x2)
- Each slider shows: METRIC NAME + current value (large number)
- Submit: Large button "SAVE ENTRY" or "UPDATE ENTRY"

Navigation: 
- Bottom bar: "DATA" | "CHARTS" | "PROFILE"
- Date navigation integrated into header
```

#### Chart Screen Layout  
```
Header:
- "3-MONTH DATA VIEW" 
- Date range display
- Metric toggles as checkboxes (not colorful pills)

Grid:
- Calendar-style layout with perfect squares
- Week abbreviations (M T W T F S S)
- Each cell shows multiple data points as small squares or bars
- Legend: Simple grayscale gradient with numbers 1-5

Controls:
- Minimal filter checkboxes
- Export button (black outline)
```

### Modern Interaction Design
- **Micro-animations**: Subtle, fast (200ms), purposeful
- **Feedback**: Immediate visual confirmation, not celebratory
- **Touch targets**: Large enough for mobile, precisely aligned
- **Loading states**: Simple black/gray spinners or progress bars
- **Error states**: Clear black text on light gray background
- **Success states**: Subtle confirmation, no green colors or confetti

## Detailed User Experience Requirements

### Data Entry Flow (Critical - Must Be Fast)
```
User opens app → See today's entry form (but can change date) → Fill sliders → Hit submit → Done
Time target: Complete daily entry in under 30 seconds

Date selection behavior:
- Default to today's date when app opens
- Show date picker/selector at top of form
- Allow user to select any past date (up to 90 days back)
- Prevent future dates (show validation error)
- When date changed, load existing data for that date (if any)
- Clear indication if data already exists: "Updating [Date]" vs "New entry for [Date]"

Navigation between dates:
- Left/right arrows to go to previous/next day
- Swipe gestures on mobile (left = yesterday, right = tomorrow)
- Date picker for jumping to specific dates
- Show visual indicator for dates that have existing data
```

### Period Tracking Logic (Must Be Clear)
```
Period toggle behavior:
- Toggle ON = "I'm on my period today"  
- When toggled ON: Show flow dropdown (spotting/light/medium/heavy)
- When toggled OFF: Hide flow dropdown, set period_flow to 'none'

New cycle creation:
- If user marks period = ON and it's been 15+ days since last period
- Auto-create new cycle with today as start_date
- Set previous cycle's end_date and is_current = false
- Set new cycle's is_current = true
```

### Chart Interaction Details
```
3-month grid requirements:
- Show exactly 90 days (not calendar months)
- Each cell represents one day
- Hover shows: "Jan 15: Energy 4/5, Mood 3/5, etc."
- Click cell to edit that day's data
- Period days: Show subtle dot or border indicator
- Missing data: Show as empty/white cells
- Future dates: Show as disabled/gray cells

Metric filtering:
- Checkboxes to show/hide each of 6 health metrics
- "Select All" / "Clear All" buttons
- Remember user's filter preferences
- Update chart immediately when filters change
```

### Authentication & User Flow (SIMPLIFIED FOR SINGLE USER)

**IMPORTANT**: This is a single-user development app. Skip complex authentication.

#### Authentication Requirements
```
Single user setup:
- NO signup/login screens
- NO email verification  
- NO password reset flows
- NO user management

Implementation options (choose simplest):
Option A: Skip auth entirely, just start logging data
Option B: Single hardcoded user in Supabase, bypass auth UI
Option C: Simple localStorage flag to simulate "logged in"

Recommended: Use Option A and add auth later if needed
```

#### App Startup Flow
```
User opens app → Immediately see today's data entry form → Start logging

That's it. No:
- Welcome screens
- App tours or tutorials  
- Profile setup forms
- Permission requests
- Loading screens with logos
- "Get started" buttons

First visit: Show empty form for today's date
Return visits: Show form with any existing data for today
```

#### Mobile Browser Optimization (PRIMARY FOCUS)

**Critical Mobile Requirements:**
```
Viewport and layout:
- Set proper viewport meta tag: width=device-width, initial-scale=1
- No horizontal scrolling ever
- App should work in Safari iOS and Chrome Android
- Optimize for portrait orientation (don't force landscape)

Touch interactions:
- All interactive elements minimum 44x44px
- No hover states (they stick on mobile)
- Use :active states instead of :hover
- Prevent zoom on input focus (font-size: 16px minimum)
- Disable text selection on sliders and buttons

Performance:
- No large images or animations
- Minimal JavaScript bundle
- Fast initial paint (<1 second)
- Smooth scrolling and interactions
```

#### Mobile-First Layout Specifications
```
Screen layout for phones (320px - 480px):
- Single column layout always
- Health metric sliders: 1 per row with large touch targets
- Period toggle: Large, easy to tap
- Submit button: Full width, bottom of form
- Navigation: Sticky bottom bar

Typography for mobile:
- Minimum 16px font size (prevents zoom)
- High contrast for outdoor use
- Large tap targets for all buttons
- Readable without glasses/contacts
```

### Data Validation & Error Handling
```
Form validation:
- All health metrics: Optional, but if provided must be 1-5
- Period flow: Required if period toggle is ON
- Entry date: Cannot be more than 90 days in past or any future date
- Show validation errors inline, not as alerts

Date handling:
- When user selects existing date: Pre-populate form with saved data
- When user selects new date: Show empty form
- Auto-save draft locally if user switches dates mid-entry
- Clear visual distinction between "new" vs "update" mode

Historical data entry:
- Allow backdating entries up to 90 days
- Show calendar view for easy date selection
- Batch entry mode (optional): Select multiple dates and copy values
```

### Performance & Loading States
```
Loading requirements:
- App must load in under 2 seconds
- Chart data loads progressively (show skeleton while loading)
- Daily form saves immediately, no loading spinner needed
- Offline support: Queue entries, sync when online

Critical performance:
- Slider interactions must be 60fps smooth
- Chart rendering under 500ms for 90 days of data
- Form submission feedback within 100ms
```

#### Mobile Browser Specific Optimizations
```
PWA features (optional but useful):
- Add to home screen capability
- Offline functionality for logging data
- App-like experience without app store

Safari iOS considerations:
- Handle safe area insets (iPhone notch)
- Prevent rubber band scrolling where not needed  
- Handle keyboard appearance/disappearance
- Test with iOS Safari's address bar behavior

Chrome Android considerations:
- Handle virtual keyboard resizing viewport
- Optimize for gesture navigation
- Test with Chrome's pull-to-refresh

Touch gestures:
- Swipe left/right to navigate between days
- Pull down to refresh data
- No complex gestures - keep it simple
```

#### Data Storage for Single User
```
Since no auth system needed:
- Skip the 'users' table entirely
- Remove user_id from all queries
- Store data directly in daily_entries and menstrual_cycles
- Use browser localStorage for any user preferences
- All database operations assume single user

Modified database queries:
// Instead of filtering by user_id, just get all data
const { data } = await supabase
  .from('daily_entries')
  .select('*')
  .order('entry_date', { ascending: false });
```

#### Simplified State Management
```
Since no auth, remove:
- Auth context/provider
- User state management  
- Login/logout functionality
- Protected routes

Keep only:
- Current entry form state
- Chart filter preferences
- Simple loading states
```

### Data Export & Backup
```
Export functionality:
- "Export Data" button in profile
- Generate CSV with columns: date, cycle_day, muscle_pain, joint_pain, etc.
- Download should work on mobile browsers
- Include last 12 months of data maximum
```

### Content & Copy Guidelines
```
App text should be:
- Clinical and precise, not casual or encouraging
- Use athletic/fitness terminology over medical jargon
- Numbers and data-focused language

Examples:
✅ "LOG DATA" (not "How are you feeling today?")
✅ "ENERGY: 4/5" (not "Energy Level")  
✅ "DAY 15 OF CYCLE" (not "Cycle Day 15")
✅ "3 DAYS SINCE PERIOD" (not "3 days since your last period")
✅ "UPDATE ENTRY" (not "Edit Today")
✅ "DATA EXPORTED" (not "Your data is ready!")

Avoid:
❌ Encouraging language like "Great job!" or "Keep it up!"
❌ Emoji or decorative punctuation
❌ Questions like "How are you feeling?"
❌ Euphemisms - use direct medical terms
```

### Navigation & Information Architecture
```
App structure (3 main screens only):
1. HOME: Today's data entry form
2. CHARTS: 3-month visualization  
3. PROFILE: User settings + export

Navigation requirements:
- Bottom tab bar on mobile (fixed position)
- Top navigation on desktop
- Active state: Black background, white text
- Icons: Minimal, geometric shapes only
- Labels: All uppercase

URL structure:
- / (home - daily entry)
- /charts (data visualization)
- /profile (settings + export)
- /login (auth)
- /signup (auth)
```

#### Single-User Database Schema Updates
```sql
-- Simplified schema without user management
-- Remove user_id references and constraints

-- Just use these tables:
menstrual_cycles (
    id UUID PRIMARY KEY,
    start_date DATE,
    end_date DATE,
    cycle_length INTEGER,
    is_current BOOLEAN,
    created_at TIMESTAMP
)

daily_entries (
    id UUID PRIMARY KEY,
    cycle_id UUID REFERENCES menstrual_cycles(id),
    entry_date DATE,
    cycle_day INTEGER,
    muscle_pain INTEGER,
    joint_pain INTEGER,
    headache INTEGER,
    energy_level INTEGER,
    sleep_quality INTEGER,
    mood INTEGER,
    period_flow VARCHAR,
    period_symptoms TEXT[],
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    UNIQUE(entry_date) -- One entry per date total
)

-- Remove all RLS policies since there's only one user
-- Remove users table entirely
```

#### Mobile Browser Testing Checklist
```
Test on actual devices:
- iPhone Safari (iOS 15+)
- Android Chrome (latest)
- Both portrait and landscape
- With/without browser address bars
- With virtual keyboard open/closed

Performance targets for mobile:
- First contentful paint: <1 second
- Time to interactive: <2 seconds  
- Slider response time: <16ms (60fps)
- Form submission: <200ms feedback

Offline behavior:
- App loads without network
- Can enter data offline
- Syncs when connection returns
- Clear offline/online status indication
```

### Specific Component Requirements
```
Slider component must have:
- Numeric input next to slider (user can type value)
- Clear visual indication of current value
- Snap to integer values only
- Keyboard navigation support

Chart component must have:
- Responsive grid layout
- Legend showing grayscale meaning
- Tooltip on hover with exact values
- Loading skeleton while data fetches
- Handle empty states gracefully

Form component requirements:
- Auto-save draft locally (localStorage)
- Validation on blur, not on every keystroke
- Clear form after successful submission
- Handle network errors gracefully
```