
# Dub Merch - Professional Women's Basketball Merchandise Aggregator

## Project Overview
**Project Name**: Dub Merch
**Description**: React Native website aggregating the best Professional Women's Basketball Player Merchandise from various sources (NOT an e-commerce site)
**Target Audience**: Women's basketball fans (ages 18-45), supporters of female athletes, WNBA enthusiasts, merchandise collectors, social justice advocates
**Core Purpose**: "Buy from the ballers, not the suits" - Direct support for athletes over corporate retailers
**Industry/Domain**: Sports merchandise aggregation, women's athletics, basketball culture
**Monetization Strategy**: Affiliate commissions from external retailer links, potential sponsored content from players/teams

## AI Tool Integration Workflow
This document serves as source of truth for:
- **Google Stitch**: High-fidelity wireframe creation (requires page-by-page instructions)
- **Figma**: Design refinement and component organization  
- **Builder.io**: Figma-to-code translation with plugin integration
- **Lovable**: Full-stack application development
- **Claude**: Database design and debugging assistance
- **Supabase**: Database management and backend services
- **GitHub**: Version control and code management
- **Vercel**: Production deployment

---

## Brand Identity & Design System

### Brand Colors (Use Exact HEX Values)
**Primary Color Palette:**
- **Primary Purple**: #330432 - Headers, brand elements, main CTAs, key messaging
- **Primary Blue**: #003153 - Navigation, body text, secondary actions, professional content
- **Primary Pink**: #CE7994 - Accent highlights, external link buttons, call-to-action elements

**Neutral Palette:**
- **Background**: #fae5da - Main page background, warm and welcoming
- **Surface**: #FFFFFF - Card backgrounds, product containers, modals
- **Text Primary**: #000000 - Primary body text, product names
- **Text Secondary**: #003153 - Supporting text, descriptions, metadata

**Semantic Colors:**
- **Success**: #28a745 - Successful link verification, positive feedback
- **Warning**: #ffc107 - Out of stock notifications, link issues
- **Error**: #dc3545 - Broken links, error messages
- **Info/Accent Blue**: #21AAE2 - Hashtags, team links, interactive elements

### Typography Hierarchy
**Font Family**: System fonts / -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif
**Scale Ratio**: 1.25 (Major Third) - Athletic and confident scaling

- **Display**: 48-64px, Primary Purple (#330432), Bold - Hero headlines, featured player names
- **H1**: 32-48px, Primary Purple (#330432), Bold - Page titles, main headers
- **H2**: 24-32px, Primary Blue (#003153), Semi-bold - Section headers, category titles
- **H3**: 18-24px, Primary Purple (#330432), Semi-bold - Product names, subsection headers
- **H4**: 16-18px, Primary Blue (#003153), Semi-bold - Card titles, player names
- **Body Large**: 16px, Primary Blue (#003153), Regular - Important descriptions, featured content
- **Body**: 14-16px, Primary Blue (#003153), Regular - Main content, product descriptions
- **Body Small**: 12-14px, Text Secondary (#003153), Regular - Team info, metadata
- **Caption**: 12px, Accent Blue (#21AAE2), Regular - Hashtags, small labels, timestamps
- **Tagline**: 12px, Primary Purple (#330432), Regular - "Buy from the ballers, not the suits"

### Component Styling Guide
**Buttons:**
- **Primary CTA**: Primary Pink (#CE7994) background, white text, 8px border radius, 12px 24px padding, subtle shadow
- **Secondary CTA**: Primary Blue (#003153) background, white text, 1px border, hover scale-105
- **External Link**: White background, Primary Pink (#CE7994) border, Primary Pink text, hover fill
- **Text Links**: Accent Blue (#21AAE2), underline on hover, smooth transition

**Interactive Elements:**
- **Product Cards**: White background, 1px light gray border, 8px border radius, hover scale-105 with shadow
- **Form Inputs**: 1px Primary Blue border, white background, Primary Pink focus outline
- **Navigation**: Primary Blue text, hover Primary Pink, active Primary Purple

**Layout Elements:**
- **Border Radius**: 8px for cards/buttons, 4px for inputs, 16px for hero elements
- **Shadows**: Light: 0 2px 4px rgba(0,0,0,0.1), Medium: 0 4px 8px rgba(0,0,0,0.15)

---

## Technical Specifications

### Layout System
- **Canvas Size**: 1440px (desktop-first design for Google Stitch)
- **Grid System**: CSS Grid with 12-column fallback, 20px gutters
- **Container Max Width**: 1200px with centered alignment
- **Spacing Scale**: 8px base unit
  - **Scale**: [8, 16, 24, 32, 48, 64, 96]px
- **Breakpoints**: 
  - **Mobile**: 320-768px (1 product per row)
  - **Tablet**: 768-1024px (2 products per row)
  - **Desktop**: 1024-1440px (3-4 products per row)
  - **Large Desktop**: 1440px+ (4+ products per row)

### Component Architecture
- **Naming Convention**: kebab-case with descriptive prefixes
  - Layout: `header-container`, `footer-section`, `product-grid-wrapper`
  - Components: `product-card-[number]`, `player-link-[name]`, `team-badge-[team]`
  - Interactive: `cta-button-external`, `nav-menu-mobile`, `search-filter-bar`

---

## Information Architecture & User Flows

### Site Map
**Core Pages (Required):**
1. **Home Page** - Featured products grid with infinite scroll, hero section with tagline
2. **Product Detail Page** - Individual product showcase with external shopping links
3. **Player Page** - All merchandise for specific player (future enhancement)

**Secondary Pages:**
- **Team Pages** - Filter by WNBA team (future enhancement)
- **About Page** - Mission statement, "buy from ballers" philosophy

**Utility Pages:**
- **Loading States** - Skeleton screens for product loading
- **404 Error** - "This baller's merch moved to a new court" themed error
- **Offline Mode** - Basic functionality when connection is poor

### Key User Flows
**Primary Flow 1**: Browse and Discover Products
Home Page → Scroll through products → Click product card → View details → Click external link → Purchase on retailer site

**Primary Flow 2**: Find Specific Player Merchandise  
Home Page → Search/Filter by player → Browse results → Select product → External purchase

**Primary Flow 3**: Team-Based Shopping
Home Page → Filter by team → Browse team products → Select items → External purchase

---

## Page-by-Page Wireframe Instructions

### Page 1: Home Page
**Google Stitch Prompt**: "Create a high-fidelity wireframe for the home page with the following exact specifications:"

#### Header Section (80px height)
**Desktop Layout:**
- **Logo**: Large "Dub Merch" wordmark, top left corner (24px height)
- **Tagline**: "Buy from the ballers, not the suits." (12px, Primary Purple, positioned right below logo)
- **Navigation Menu**: Home, Players, Teams, Featured, About, Contact (Primary Blue, horizontal layout)
- **Search Bar**: Optional search functionality (right side of header)
- **Sticky Behavior**: Yes - header stays fixed while scrolling

**Mobile Layout:**
- **Logo**: "Dub Merch" (20px height, top left)
- **Tagline**: Same text, smaller and stacked below logo
- **Hamburger Menu**: ☰ icon (top right) containing all navigation items
- **Search**: Collapsible search bar or separate search page

#### Hero/Primary Section (400px height)
- **Headline**: "Shop Directly From Your Favorite WNBA Players"
- **Subheadline**: "Discover authentic merchandise that puts money back in the pockets of the women changing the game"
- **Call-to-Action**: "Browse Player Merch" button (Primary Pink style)
- **Visual Element**: Collage of popular WNBA players or action shots
- **Background**: Subtle gradient from Background color (#fae5da) to white

#### Main Content Section - Product Grid
**Layout Pattern**: Responsive CSS Grid with infinite scroll
- **Desktop**: 3-4 products per row with 32px gaps
- **Tablet**: 2 products per row with 24px gaps  
- **Mobile**: 1 product per row with 16px gaps

**Product Cards Structure (9 initial products):**
1. **A'ja Wilson Signature Sneakers** - Las Vegas Aces
   - Colored dot (Las Vegas Aces team colors) + Product Name (18px, Primary Purple)
   - "Las Vegas Aces" (14px, Primary Blue, indented)
   - "A'ja Wilson - MVP Center" (12px, gray text, indented)
   - "#LasVegasAces #MVP #Sneakers #Basketball" (12px, Accent Blue)

2. **Breanna Stewart Practice Jersey** - New York Liberty
   - Green dot + Product Name
   - "New York Liberty" (14px, Primary Blue)
   - "Breanna Stewart - Forward" (12px, gray)
   - "#NewYorkLiberty #Champion #Jersey #WNBA"

3. **Diana Taurasi Vintage Tee** - Phoenix Mercury
   - Orange dot + Product Name  
   - "Phoenix Mercury" (14px, Primary Blue)
   - "Diana Taurasi - Guard Legend" (12px, gray)
   - "#PhoenixMercury #GOAT #Vintage #Basketball"

4. **Candace Parker Hoodie** - Chicago Sky
   - Blue dot + Product Name
   - "Chicago Sky" (14px, Primary Blue)
   - "Candace Parker - Forward" (12px, gray)
   - "#ChicagoSky #Legend #Hoodie #ComfortWear"

5. **Sue Bird Retirement Cap** - Seattle Storm
   - Green dot + Product Name
   - "Seattle Storm" (14px, Primary Blue) 
   - "Sue Bird - Retired Point Guard" (12px, gray)
   - "#SeattleStorm #Retired #Legacy #Cap"

6. **Sabrina Ionescu Youth Jersey** - New York Liberty
   - Green dot + Product Name
   - "New York Liberty" (14px, Primary Blue)
   - "Sabrina Ionescu - Guard" (12px, gray)
   - "#NewYorkLiberty #Youth #Rising #Jersey"

7. **Kelsey Plum Training Shorts** - Las Vegas Aces  
   - Gold dot + Product Name
   - "Las Vegas Aces" (14px, Primary Blue)
   - "Kelsey Plum - Guard" (12px, gray)
   - "#LasVegasAces #AllStar #Training #ActiveWear"

8. **Alyssa Thomas Warm-up Jacket** - Connecticut Sun
   - Orange dot + Product Name
   - "Connecticut Sun" (14px, Primary Blue)
   - "Alyssa Thomas - Forward" (12px, gray)
   - "#ConnecticutSun #Defense #Warmup #Training"

9. **Nneka Ogwumike Signature Basketball** - Seattle Storm
   - Green dot + Product Name
   - "Seattle Storm" (14px, Primary Blue)
   - "Nneka Ogwumike - Forward" (12px, gray)
   - "#SeattleStorm #Veteran #Basketball #Equipment"

**Card Design Elements:**
- Thin team-colored accent stripe at top (4px height)
- Square (1:1 aspect ratio) product image with skeleton loading placeholder
- White background with subtle shadow on hover
- "Shop External" button (white background, Primary Pink border and text)
- Hover effects: transform scale-105 with increased shadow
- Touch targets: 44px minimum height for mobile buttons

#### Infinite Scroll Section
- **Loading Indicators**: Subtle spinner with "Loading more products..." text
- **End State**: "You've seen all available products! Check back soon for new drops."
- **Performance**: Lazy load images, preload next 6 products

#### Footer Section (150px height)
- **Background**: Primary Purple (#330432)
- **Text Color**: Background color (#fae5da) for warmth
- **Content**: 
  - "About Dub Merch" link
  - "Support Players Directly" mission statement
  - Social media links (if applicable)
  - Contact information
  - "Built for ballers, by ballers" tagline

### Page 2: Product Detail Page
**Google Stitch Prompt**: "Create a high-fidelity wireframe for the product detail page with the following exact specifications:"

#### Header Section
- **Consistency**: Same header as home page with identical styling
- **Breadcrumb Navigation**: Home > [Player Name] > [Item Name]
  - Font: 12px, Accent Blue (#21AAE2) with chevron separators
  - Position: Below header, left-aligned with 16px top margin

#### Product Detail Content (Split Layout)
**Left Side - Image Gallery (60% width):**
- **Main Image**: Large square product image (600px × 600px)
- **Thumbnail Gallery**: 3 smaller images below main image (150px × 150px each)
- **Mobile Behavior**: Swipe gestures between images, thumbnail row scrollable
- **Loading States**: Blur-up effect from low-res to high-res images
- **Zoom Feature**: Click to enlarge on desktop, pinch-to-zoom on mobile

**Right Side - Product Information (40% width):**
- **Product Title**: [Player Name] + [Item Name] (32px, Primary Purple, bold)
- **Player Info**: "[Player Name] - [Position] for [Team Name]" (16px, Primary Blue)
- **Product Description**: 
  - Short 2-3 sentence description of the item
  - Material/size information if available
  - "Authentic merchandise from [Player Name]'s official collection"
  - Font: 14px, Primary Blue, line-height 1.5
- **Hashtags**: Team and player hashtags (12px, Accent Blue, organized in rows)
- **External Link Section**:
  - **Primary CTA**: "Shop on [Retailer Name]" button
    - Primary Pink background, white text, 48px height
    - Full width on mobile, 280px width on desktop
  - **Secondary Info**: "Price and availability on retailer site"
    - 12px gray text below button
- **Additional Links**: "View More from [Player Name]" (future enhancement)

#### Footer Section
- **Same as Home Page**: Consistent footer design and content

---

## Content Strategy & Sample Data

### Content Tone & Voice
**Brand Personality**: Empowering, authentic, community-driven, sports-passionate
**Tone Attributes**: Conversational but respectful, optimistic, inclusive, action-oriented
**Language Style**: Simple and accessible, avoiding jargon, celebrating athletes

### Sample Content Templates
**Product Descriptions:**
- "Authentic [item type] from [Player Name]'s personal collection"
- "Show your support for [Player Name] and the [Team Name] with this [item]"
- "Quality [item type] that represents the excellence [Player Name] brings to the court"

**Call-to-Action Copy:**
- "Shop Direct" / "Shop on [Retailer]" / "Support [Player Name]"
- "Buy from the Baller" / "Get Yours Now" / "Shop Authentic"

**Error/Loading States:**
- Loading: "Finding the freshest drops..." / "Loading player merchandise..."
- Error: "This link took a timeout! Try again." / "Can't connect to the store right now"
- Empty: "No merch found for this search. Try browsing all products!"

---

## Database Schema & Backend Architecture

### Core Data Entities
```sql
-- Players table
Table: players
- id: uuid (Primary Key)
- name: varchar(100) NOT NULL
- team_id: uuid REFERENCES teams(id)
- position: varchar(20) -- Guard, Forward, Center
- jersey_number: integer
- active_status: boolean DEFAULT true
- bio: text -- Short player description
- image_url: varchar(500) -- Player headshot
- social_links: jsonb -- Social media handles
- created_at: timestamp with time zone
- updated_at: timestamp with time zone

-- Teams table  
Table: teams
- id: uuid (Primary Key)
- name: varchar(100) NOT NULL -- "Las Vegas Aces"
- abbreviation: varchar(5) -- "LVA"
- primary_color: varchar(7) -- Hex color for team branding
- secondary_color: varchar(7) -- Secondary team color
- league: varchar(50) DEFAULT 'WNBA'
- city: varchar(100) NOT NULL
- founded_year: integer
- logo_url: varchar(500)
- created_at: timestamp with time zone

-- Products table
Table: products
- id: uuid (Primary Key)
- name: varchar(200) NOT NULL -- "Signature Sneakers"
- player_id: uuid REFERENCES players(id)
- team_id: uuid REFERENCES teams(id) -- For team-specific merchandise
- category: varchar(50) -- Apparel, Footwear, Accessories, Equipment
- description: text
- external_url: varchar(500) NOT NULL -- Link to retailer
- retailer_name: varchar(100) -- Nike, Fanatics, etc.
- image_urls: jsonb -- Array of product image URLs
- featured: boolean DEFAULT false
- active: boolean DEFAULT true -- For discontinued products
- price_range: varchar(20) -- "$50-75" (since prices change externally)
- created_at: timestamp with time zone
- updated_at: timestamp with time zone
- last_verified: timestamp with time zone -- When link was last checked

-- Product Tags (for hashtags and filtering)
Table: product_tags
- id: uuid (Primary Key)
- product_id: uuid REFERENCES products(id) ON DELETE CASCADE
- tag_name: varchar(50) NOT NULL -- "MVP", "Championship", "Rookie"
- tag_type: varchar(20) -- "achievement", "style", "team", "player"

-- User Favorites (future enhancement)
Table: user_favorites
- id: uuid (Primary Key)
- user_id: uuid -- Future user system integration
- product_id: uuid REFERENCES products(id) ON DELETE CASCADE
- created_at: timestamp with time zone

Relationships:
- products.player_id -> players.id (one-to-many)
- products.team_id -> teams.id (one-to-many)  
- players.team_id -> teams.id (many-to-one)
- product_tags.product_id -> products.id (many-to-many through junction)
```


---

## Performance & Optimization Requirements

### Image Strategy
- **Primary Format**: WebP with JPG fallbacks for broader compatibility
- **Sizing Strategy**: Responsive images with srcset for different device sizes
  - Product cards: 400px, 600px, 800px widths
  - Detail page: 600px, 900px, 1200px widths
- **Loading Strategy**: 
  - Above-fold images: Eager loading with high priority
  - Product grid: Lazy loading with intersection observer
  - Detail page: Progressive loading from blur to sharp
- **Optimization**: 85% JPEG quality, aggressive WebP compression, CDN delivery

### Loading States & Error Handling
**Loading Patterns:**
- **Skeleton Screens**: Product grid cards with animated placeholders
- **Spinners**: Infinite scroll loading, search results
- **Progressive Loading**: Hero images, product detail galleries

**Error Handling:**
- **Broken Product Links**: Gray out product with "Link temporarily unavailable" message
- **Network Errors**: Retry button with "Check your connection" message
- **Search No Results**: "No merch found, but check out these popular items" with fallback products
- **404 Pages**: Basketball-themed "This play doesn't exist" with navigation back to home

### Accessibility Requirements
- **WCAG Level**: AA compliance throughout
- **Keyboard Navigation**: Full site navigable without mouse, proper focus indicators
- **Screen Readers**: Alt text for all product images, ARIA labels for interactive elements
- **Color Contrast**: All text meets 4.5:1 contrast ratio against backgrounds
- **Touch Targets**: 44px minimum for all buttons and links on mobile devices

---

## Mobile Experience Specifications

### Responsive Breakpoints & Behavior
**Mobile (320-768px):**
- **Navigation**: Hamburger menu with slide-out drawer
- **Product Grid**: Single column with full-width cards
- **Touch Interactions**: Swipe gestures for image galleries, pull-to-refresh for product updates
- **Header**: Condensed logo, collapsible search

**Tablet (768-1024px):**
- **Layout**: 2-column product grid, expanded header
- **Navigation**: Horizontal menu with condensed spacing
- **Images**: Larger product cards with better image quality

### Mobile-Specific Features
- **Gestures**: 
  - Left/right swipe on product detail image gallery
  - Pull-to-refresh on home page product grid
  - Pinch-to-zoom on product detail images
- **Performance**: 
  - Aggressive image compression for mobile
  - Reduced animations to improve battery life
  - Lazy loading with smaller buffer for slower connections

---
---
---

# Extra items

## Project Success Metrics

### Business Metrics
- **Primary Goal**: Generate affiliate revenue while supporting female athletes
- **Secondary Goals**: Build engaged community of WNBA merchandise enthusiasts
- **Key Performance Indicators**:
  - External link click-through rate (target: 15%+)
  - User session duration (target: 3+ minutes average)
  - Mobile traffic percentage (target: 60%+ of total traffic)
  - Product discovery rate (products viewed per session: 8+)
  - User return rate (target: 25% returning visitors)

### Technical Metrics  
- **Performance**: Core Web Vitals - LCP <2.5s, FID <100ms, CLS <0.1
- **Reliability**: 99.5% uptime, error rate <1% of all requests
- **User Experience**: Accessibility score 95+, mobile performance score 90+

### Timeline & Milestones
- **MVP Definition**: Home page with 9 products, basic product detail pages, mobile responsive
- **Phase 1** (Week 1-2): Core wireframes, database setup, basic React components
- **Phase 2** (Week 3-4): Product detail pages, search functionality, infinite scroll
- **Launch** (Week 5): Production deployment, analytics setup, performance optimization

## AI Tool Integration Notes

### Google Stitch Instructions
**Always specify exactly:**
- "Create high-fidelity wireframes for [Home Page / Product Detail Page]"
- Canvas width: 1440px for desktop-first design
- Component grouping: `product-card-[1-9]`, `header-container`, `footer-section`
- Exact measurements: Header 80px, Footer 150px, Hero section 400px
- Specific product content: All 9 products with exact names, teams, and hashtags
- Color specifications: Use exact hex values for all branded elements

**Critical Note**: Google Stitch only creates home pages by default - explicitly request "Product Detail Page" as separate wireframe.

### Lovable Development Notes
**Provide before code generation:**
- Complete Supabase schema with all table relationships
- All 9 sample products as seed data for realistic testing
- API endpoint structure for products, players, and teams
- Component specifications matching Builder.io naming convention
- Mobile-first responsive requirements with specific breakpoints

**Request specifically:**
- TypeScript implementation with strict typing for all data models
- Error boundary components for graceful failure handling
- Infinite scroll implementation with Intersection Observer API
- Image lazy loading with skeleton placeholder components
- Accessibility compliance: semantic HTML, ARIA labels, keyboard navigation
- Performance optimization: image compression, bundle splitting, CDN integration

### Claude Code Assistance
**Primary use cases:**
- Database query optimization for complex product filtering by player/team
- Performance analysis for infinite scroll and image loading bottlenecks
- Accessibility audit and remediation for WCAG AA compliance
- Mobile responsive debugging for complex CSS Grid layouts
- API endpoint optimization for search and filtering functionality
- Link verification system for monitoring external affiliate URLs

### Builder.io Integration
**Component Export Requirements:**
- Semantic HTML structure: `<article>` for product cards, `<nav>` for navigation
- Consistent naming: All components use kebab-case with descriptive prefixes
- Proper component hierarchy: Cards contain images, titles, descriptions, and CTAs
- Interactive state definitions: Hover effects, focus states, loading placeholders
- Mobile-responsive classes: Tailwind utilities for all breakpoint behaviors


## Deployment & DevOps Configuration

### Environment Setup
```bash
# Core Application
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
NEXT_PUBLIC_SITE_URL=https://dubmerch.com

# Analytics & Monitoring
NEXT_PUBLIC_GA_MEASUREMENT_ID=G-XXXXXXXXXX
VERCEL_ANALYTICS_ID=your-vercel-analytics-id

# External Services (Future)
AFFILIATE_API_KEY=your-affiliate-network-key
IMAGE_CDN_URL=https://images.dubmerch.com
LINK_CHECKER_API_KEY=your-link-verification-service

# Development
NODE_ENV=production
DATABASE_URL=postgresql://connection-string
```

### Deployment Configuration
**Vercel Settings:**
- **Framework**: Next.js 14+ with App Router
- **Build Command**: npm run build
- **Output Directory**: .next
- **Node Version**: 18.x (LTS)
- **Environment Variables**: All variables from template above
- **Custom Domains**: dubmerch.com, www.dubmerch.com
- **Analytics**: Vercel Analytics enabled for performance monitoring

### Version Control Strategy
**Branch Structure:**
- `main` - Production deployment, protected branch
- `staging` - Pre-production testing environment  
- `develop` - Integration branch for feature development
- `feature/player-pages` - Individual feature development
- `hotfix/broken-links` - Emergency fixes for production issues

**Commit Message Convention:**
- `feat: add player filtering to product grid`
- `fix: resolve mobile image loading issue`
- `docs: update API endpoint documentation`
- `style: improve mobile navigation spacing`
- `refactor: optimize product card component`
- `test: add unit tests for search functionality`


---
## Quality Assurance Checklist

### Design Verification
- [ ] Brand colors (#330432, #003153, #CE7994, #fae5da, #21AAE2) applied consistently
- [ ] Typography hierarchy follows 1.25 scale ratio with proper contrast
- [ ] Component naming follows kebab-case convention with descriptive prefixes
- [ ] All interactive states (hover, focus, active, disabled) defined for buttons and links
- [ ] Loading skeleton screens designed for product grid and detail pages
- [ ] Error states include basketball-themed messaging with helpful actions
- [ ] Mobile responsive design works across 320px to 1440px+ viewports
- [ ] Accessibility: 44px touch targets, proper contrast ratios, keyboard navigation

### Content Verification
- [ ] All 9 sample products feature realistic WNBA players and teams
- [ ] Team colors and hashtags accurately represent actual WNBA teams
- [ ] Product names and categories reflect authentic sports merchandise
- [ ] "Buy from the ballers, not the suits" tagline prominently featured
- [ ] Copy tone supports female athletes and empowerment messaging
- [ ] Basketball terminology used appropriately throughout

### Technical Verification
- [ ] Database schema supports player-team relationships and product categorization
- [ ] API endpoints planned for all filtering and search functionality
- [ ] External link verification system designed for affiliate link management
- [ ] Infinite scroll implementation planned with proper loading states
- [ ] Image optimization strategy supports multiple device sizes and connections
- [ ] Performance considerations include lazy loading and CDN integration


### API Endpoints
```
Core Product APIs:
GET /api/products - List all products (paginated, with filters)
GET /api/products/[id] - Get single product with full details
GET /api/products/featured - Get featured/highlighted products
GET /api/products/player/[playerId] - Get all products for specific player
GET /api/products/team/[teamId] - Get all products for specific team

Search & Filtering:
GET /api/search?q=[query] - Search products by name, player, team
GET /api/products?category=[category] - Filter by product category
GET /api/products?tags=[tag1,tag2] - Filter by hashtags/tags

Player & Team Data:
GET /api/players - List all players with basic info
GET /api/players/[id] - Get player details with product count
GET /api/teams - List all WNBA teams
GET /api/teams/[id] - Get team details with players and products

Link Management (Admin):
POST /api/admin/products/verify-links - Batch verify external URLs
GET /api/admin/products/broken-links - Get products with broken external links
```
