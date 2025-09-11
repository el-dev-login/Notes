# [PROJECT NAME] - AI-Powered Development Guidelines

## Project Overview
<!-- Claude: Ask about the project's core purpose, target users, and main features -->
**Project Name**: [PROJECT NAME]
**Description**: [1-2 sentence description of what the application does and its primary function]
**Target Audience**: [Primary user demographic - be specific about age, interests, profession, etc.]
**Core Purpose**: [Main value proposition - what problem does this solve?]
**Industry/Domain**: [e.g., E-commerce, Education, Healthcare, Entertainment, etc.]
**Monetization Strategy**: [How does the business make money? Subscription, ads, marketplace, etc.]

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

<!-- Claude: Help determine brand colors based on industry, target audience, and desired emotional response -->
### Brand Colors
**Primary Color Palette:**
- **Primary**: [HEX] - [When to use: headers, main CTAs, brand elements]
- **Secondary**: [HEX] - [When to use: secondary actions, accents]
- **Accent**: [HEX] - [When to use: highlights, notifications, special elements]

**Neutral Palette:**
- **Background**: [HEX] - [Main page background]
- **Surface**: [HEX] - [Card backgrounds, modals]
- **Text Primary**: [HEX] - [Main body text]
- **Text Secondary**: [HEX] - [Supporting text, captions]

**Semantic Colors:**
- **Success**: [HEX] - [Success messages, completed states]
- **Warning**: [HEX] - [Warning messages, caution states]
- **Error**: [HEX] - [Error messages, destructive actions]
- **Info**: [HEX] - [Information messages, neutral notifications]

<!-- Claude: Create typography scale based on brand personality (modern, traditional, playful, etc.) -->
### Typography Hierarchy
**Font Family**: [Primary font] / [Fallback fonts]
**Scale Ratio**: [1.25 (Major Third) / 1.333 (Perfect Fourth) / 1.414 (Major Second) / etc.]

- **Display**: [Size]px, [Color], [Weight] - Large marketing text, hero headlines
- **H1**: [Size]px, [Color], [Weight] - Page titles, main headers
- **H2**: [Size]px, [Color], [Weight] - Section headers
- **H3**: [Size]px, [Color], [Weight] - Subsection headers
- **H4**: [Size]px, [Color], [Weight] - Card titles, smaller headers
- **Body Large**: [Size]px, [Color], [Weight] - Important body text
- **Body**: [Size]px, [Color], [Weight] - Main content
- **Body Small**: [Size]px, [Color], [Weight] - Supporting content
- **Caption**: [Size]px, [Color], [Weight] - Small text, labels, metadata

<!-- Claude: Design component styles based on brand personality and user expectations -->
### Component Styling Guide
**Buttons:**
- **Primary CTA**: [Background], [Text color], [Border radius], [Padding], [Shadow]
- **Secondary CTA**: [Background], [Text color], [Border], [Hover state]
- **Tertiary/Ghost**: [Background], [Text color], [Border], [Hover state]
- **Destructive**: [Background], [Text color] - For delete/remove actions

**Interactive Elements:**
- **Links**: [Color], [Hover state], [Underline: Yes/No]
- **Form Inputs**: [Border], [Background], [Focus state], [Error state]
- **Cards**: [Background], [Border], [Shadow], [Border radius], [Hover state]

**Layout Elements:**
- **Border Radius**: [Size]px for buttons, [Size]px for cards, [Size]px for inputs
- **Shadows**: Light: [shadow values], Medium: [shadow values], Heavy: [shadow values]

---

## Technical Specifications

<!-- Claude: Recommend grid system and spacing based on project complexity and responsive needs -->
### Layout System
- **Canvas Size**: [1440px (desktop-first) / 375px (mobile-first)]
- **Grid System**: [12-column / 16-column / CSS Grid] with [X]px gutters
- **Container Max Width**: [1200px / 1440px / fluid]
- **Spacing Scale**: [X]px base unit
  - **Scale**: [4, 8, 16, 24, 32, 48, 64, 96]px OR [rem values]
- **Breakpoints**: 
  - **Mobile**: 320-768px
  - **Tablet**: 768-1024px
  - **Desktop**: 1024-1440px
  - **Large Desktop**: 1440px+

### Component Architecture
- **Naming Convention**: [Choose: BEM, kebab-case, camelCase] - [prefix]-[component]-[element]--[modifier]
- **Component Categories**: 
  - Layout: [header, footer, sidebar, container, grid]
  - Navigation: [navbar, breadcrumb, pagination, tabs]
  - Content: [card, article, hero, banner]
  - Forms: [input, button, checkbox, select]
  - Feedback: [modal, toast, loading, error]

---

## Information Architecture & User Flows

<!-- Claude: Help map out all necessary pages and user journeys -->
### Site Map
**Core Pages (Required):**
1. [Page Name] - [Purpose and main content]
2. [Page Name] - [Purpose and main content]
3. [Page Name] - [Purpose and main content]

**Secondary Pages:**
- [Page Name] - [Purpose]
- [Page Name] - [Purpose]

**Utility Pages:**
- Loading/Splash Screen
- 404 Error Page
- 500 Error Page
- Maintenance Mode

### Key User Flows
**Primary Flow 1**: [User Goal]
[Step 1] → [Step 2] → [Step 3] → [Completion]

**Primary Flow 2**: [User Goal]  
[Step 1] → [Step 2] → [Step 3] → [Completion]

---

## Page-by-Page Wireframe Instructions

<!-- Claude: Generate detailed specifications for each page based on user flows and content needs -->

### Page 1: [Page Name] (e.g., Home/Landing Page)
**Google Stitch Prompt**: "Create a high-fidelity wireframe for the [page name] with the following exact specifications:"

#### Header Section ([X]px height)
**Desktop Layout:**
- **Logo**: [Size and placement]
- **Navigation Menu**: [List menu items: Item 1, Item 2, Item 3, etc.]
- **User Actions**: [Login/Signup, Cart, Search, Profile, etc.]
- **Sticky Behavior**: [Yes/No and behavior description]

**Mobile Layout:**
- **Logo**: [Size and placement]
- **Hamburger Menu**: Contains [list all menu items]
- **Priority Actions**: [Which buttons stay visible on mobile]

#### Hero/Primary Section ([X]px height)
- **Headline**: "[Exact headline text or placeholder style]"
- **Subheadline**: "[Supporting text or description]"
- **Call-to-Action**: "[Button text]" - [Button style from design system]
- **Visual Element**: [Hero image, video, illustration, product showcase]
- **Background**: [Color, image, gradient]

#### Content Sections
**Section 1: [Name]**
- **Purpose**: [What this section achieves]
- **Layout**: [Grid, list, carousel, etc.]
- **Content Type**: [Cards, text blocks, images, testimonials]
- **Specific Elements**: [Detailed list of what appears here]

**Section 2: [Name]**
- [Repeat structure]

#### Footer Section ([X]px height)
- **Links**: [Categorized list of footer links]
- **Contact Info**: [What contact information to include]
- **Legal**: [Privacy Policy, Terms, etc.]
- **Social Media**: [Which platforms to link]

### Page 2: [Second Page Name]
**Google Stitch Prompt**: "Create a high-fidelity wireframe for [page name] with the following exact specifications:"

#### Header
- **Consistency**: [Same as home / Modified version]
- **Breadcrumbs**: [Yes/No and format]
- **Page-Specific Elements**: [Search bars, filters, etc.]

#### Main Content Area
- **Layout Pattern**: [List, grid, single column, sidebar, etc.]
- **Primary Content**: [Detailed description of main content]
- **Secondary Content**: [Sidebars, related items, etc.]
- **Interactive Elements**: [Filters, sorting, pagination, etc.]

#### [Continue for each page]

---

## Content Strategy & Sample Data

<!-- Claude: Generate realistic content that matches the project's domain and target audience -->

### Content Tone & Voice
**Brand Personality**: [Professional, Friendly, Authoritative, Playful, etc.]
**Tone Attributes**: [Conversational/Formal, Optimistic/Serious, etc.]
**Language Style**: [Simple/Technical, Inclusive, Action-oriented, etc.]

### Sample Content Blocks
<!-- Claude: Create realistic sample content for each content type -->

**[Content Type 1] Examples:**
1. [Sample item with realistic details]
2. [Sample item with realistic details]
3. [Sample item with realistic details]

**Copy Templates:**
- **Headlines**: "[Template with variables]"
- **CTAs**: "[Action verb] + [value proposition]"
- **Descriptions**: "[Format and length guidelines]"

---

## Database Schema & Backend Architecture

<!-- Claude: Design database schema based on user flows and content requirements -->

### Core Data Entities
```sql
-- Primary Entity
Table: [table_name]
- id: [uuid/serial] (Primary Key)
- [field]: [type] [constraints] -- [Purpose/description]
- [field]: [type] [constraints] -- [Purpose/description]
- created_at: timestamp with time zone
- updated_at: timestamp with time zone
- [soft_delete_field]: boolean DEFAULT false

-- Related Entity
Table: [related_table]
- id: [type] (Primary Key)
- [foreign_key]: [type] REFERENCES [table_name](id)
- [additional_fields]: [type] [constraints]

-- Junction Table (if many-to-many relationships exist)
Table: [junction_table]
- [entity_1]_id: [type] REFERENCES [table_1](id)
- [entity_2]_id: [type] REFERENCES [table_2](id)
- PRIMARY KEY ([entity_1]_id, [entity_2]_id)
```





## Mobile Experience Specifications

<!-- Claude: Design mobile-first interactions and responsive behavior -->

### Responsive Breakpoints & Behavior
**Mobile (320-768px):**
- **Navigation**: [Hamburger menu / Bottom navigation / etc.]
- **Grid**: [Single column / 2-column for specific content]
- **Touch Interactions**: [Swipe gestures, pull-to-refresh, etc.]

**Tablet (768-1024px):**
- **Layout**: [Hybrid mobile/desktop approach]
- **Navigation**: [Expanded or collapsed menu]

### Mobile-Specific Features
- **Gestures**: [Swipe, pinch-to-zoom, pull-to-refresh, etc.]
- **Native Features**: [Camera, location, push notifications, etc.]
- **Performance**: [Lazy loading, image compression, reduced animations]

---

## Deployment & DevOps Configuration

### Environment Setup
```bash
# Environment Variables Template
NEXT_PUBLIC_SUPABASE_URL=your-supabase-project-url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-supabase-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
NEXT_PUBLIC_SITE_URL=https://your-domain.com
DATABASE_URL=your-database-connection-string

# Optional Third-party Services
NEXT_PUBLIC_ANALYTICS_ID=your-analytics-id
STRIPE_SECRET_KEY=your-stripe-key (if e-commerce)
RESEND_API_KEY=your-email-service-key
```

### Deployment Configuration
**Vercel Settings:**
- **Framework**: [Next.js / React / Vue.js / etc.]
- **Build Command**: [npm run build / yarn build]
- **Output Directory**: [.next / dist / build]
- **Node Version**: [18.x / 20.x / latest LTS]
- **Environment Variables**: [List all required env vars]

### Version Control Strategy
**Branch Structure:**
- `main` - Production-ready, auto-deploys to production
- `staging` - Pre-production testing, auto-deploys to staging
- `develop` - Development integration branch
- `feature/[feature-name]` - Feature development branches
- `hotfix/[issue-description]` - Emergency production fixes

**Commit Message Convention:**
- `feat:` New features and enhancements
- `fix:` Bug fixes and patches
- `docs:` Documentation updates
- `style:` Code formatting and style changes
- `refactor:` Code improvements without feature changes
- `test:` Testing additions and updates
- `chore:` Build process and tooling updates

---


<!-- 
CLAUDE COMPLETION INSTRUCTIONS:
When helping populate this template, ask clarifying questions about:
1. Project purpose and target audience specifics
2. Industry/domain context for appropriate design decisions
3. Technical complexity and feature requirements
4. Content types and user interaction patterns
5. Business model and success metrics
6. Timeline and resource constraints

Focus on generating realistic, detailed content rather than generic placeholders.
Provide rationale for design decisions based on best practices and user experience principles.
-->



