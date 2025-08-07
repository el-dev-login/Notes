**Add your own guidelines here**

# General Guidelines
* Only use absolute positioning when necessary. Opt for responsive and well structured layouts that use flexbox and grid by default
* Refactor code as you go to keep code clean
* Keep file sizes small and put helper functions and components in their own files.
* Only keep component files that are used. Delete unused files. 

# Code guidelines

Use this file structure
```
your-website/
├── src/
│   ├── App.tsx                     # Main component
│   ├── components/
|   │   ├── figma/
|   │   └── ui/                     # ShadCN components library
│   ├── imports/                    # Figma-imported SVG assets
│   └── styles/
|       └── globals.css             # Tailwind v4 + design tokens
├── public/
│   └── images/                     # Your hosted product images
└── Guidelines.md                   # This file
```

# Key Files to Monitor:
- `Guidelines.md` - Your design system source of truth
- `App.tsx` - Main component with all logic
- `./imports/svg-9r0wl0ln1p.ts` - Logo SVG assets
- `styles/globals.css` - Tailwind configuration


# Design System 

## Brand Colors
- Primary Purple: #330432
- Primary Blue: #003153  
- Primary Pink: #CE7994
- Background: #fae5da
- Accent Blue: #21AAE2


## Layout Rules
- First row: 2 items maximum
- Subsequent rows: 3 items maximum
- Product images: 4:3 aspect ratio (landscape)

#### Spacing/Grid System
- Grid gap: `2rem` (gap-8)
- Container: `max-w-7xl mx-auto px-6`
- Logo container: `max-w-4xl` with `h-64`


## Component Rules

#### Component Library
- **ProductCard**: 4:3 aspect ratio, accent color stripe, hover effects
- **Navigation**: Colored dots + labels, active/inactive states
- **SiteLogo**: SVG with decorative accent dots
- **CustomProductGrid**: 2-item first row, 3-item subsequent rows

### Current Component Structure
- SiteLogo(): Logo with decorative dots
- ProductCard(): Individual product display
- CustomProductGrid(): Handles 2-3 layout logic
- App(): Main container with state management
- **Hover Effects**: scale-105 + 20% black overlay

### SiteLogo
- SVG height: h-64, max-width: max-w-4xl
- Use imported SVG paths from svg-9r0wl0ln1p.ts

### ProductCard
- Always include accent color stripe at top (h-1)
- Hover effects: scale-105 + 20% black overlay
- Button style: white bg, colored border matching accent
- Image aspect ratio: aspect-[4/3]
- Product info layout: dot + name, then team/player indented

### Navigation
- Include colored dots next to labels (w-2 h-2)
- Active state: underline + full opacity dot
- Inactive state: 50% opacity dot
- Font: Tenor Sans, 24px, -0.72px tracking

## Typography
- Navigation: font-['Tenor_Sans:Regular',_sans-serif] text-[24px] tracking-[-0.72px]
- Product names: Default system typography (no font size classes)
- Team info: text-sm text-gray-600
- Player info: text-sm text-gray-500
- **Typography**: Tenor Sans for nav, system defaults for content

## Assets
- Logo: Always use imported SVG paths 
- Product images: Use ImageWithFallback component. Import JPEG images. Do not reference images. 
- All icons: Lucide React
- Image dimensions: 600x450 (4:3 landscape)


#### Asset Library
- Logo SVG paths (imported from Figma)
- Accent dots (CSS-generated circles)
- Product images (Unsplash placeholder → your hosted images)

<!-- Things to add

SVG images should be converted to react component files and imported
JPGs should be imported
Import images rather than using public folder when possible - it enables webpack optimizations
-->


<!-- Design system example guidelines



## Button
The Button component is a fundamental interactive element in our design system, designed to trigger actions or navigate
users through the application. It provides visual feedback and clear affordances to enhance user experience.

### Usage
Buttons should be used for important actions that users need to take, such as form submissions, confirming choices,
or initiating processes. They communicate interactivity and should have clear, action-oriented labels.

### Variants
* Primary Button
  * Purpose : Used for the main action in a section or page
  * Visual Style : Bold, filled with the primary brand color
  * Usage : One primary button per section to guide users toward the most important action
* Secondary Button
  * Purpose : Used for alternative or supporting actions
  * Visual Style : Outlined with the primary color, transparent background
  * Usage : Can appear alongside a primary button for less important actions
* Tertiary Button
  * Purpose : Used for the least important actions
  * Visual Style : Text-only with no border, using primary color
  * Usage : For actions that should be available but not emphasized
-->
