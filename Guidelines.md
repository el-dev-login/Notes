**Purpose** This file is for telling the AI Agent guidelines on development. 

# General Guidelines
* Only use absolute positioning when necessary. Opt for responsive and well structured layouts that use flexbox and grid by default
* Refactor code as you go to keep code clean
* Keep file sizes small and put helper functions and components in their own files.
* Only keep component files that are used. Delete unused files. 

# File Structure

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

# Code Guidelines


# Key Files to Monitor
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




### Shadcn/ui & Tailwind references

- Tailwind CSS Cheat Sheet: https://www.creative-tim.com/twcomponents/cheatsheet
- Tailwind Docs: https://tailwindcss.com/docs/installation/using-vite



### Using shadcn/ui in Figma




### Shadcn/ui theme to paste into Figma plugin

Can't figure out how to move a design system from one variable collection to another for colors. 

@layer base {
    :root {
      --background: 242 53% 99%;
      --foreground: 242 55% 1%;
      --muted: 242 25% 91%;
      --muted-foreground: 242 11% 27%;
      --popover: 242 53% 98%;
      --popover-foreground: 0 0% 0%;
      --card: 242 53% 98%;
      --card-foreground: 0 0% 0%;
      --border: 242 2% 89%;
      --input: 242 2% 89%;
      --primary: 242 70% 25%;
      --primary-foreground: 242 70% 85%;
      --secondary: 242 9% 82%;
      --secondary-foreground: 242 9% 22%;
      --accent: 242 9% 82%;
      --accent-foreground: 242 9% 22%;
      --destructive: 6 85% 25%;
      --destructive-foreground: 6 85% 85%;
      --ring: 242 70% 25%;
      --chart-1: 242 70% 25%;
      --chart-2: 242 9% 82%;
      --chart-3: 242 9% 82%;
      --chart-4: 242 9% 85%;
      --chart-5: 242 73% 25%;
      --radius: 0.5rem;
    }
  
    .dark {
      --background: 242 60% 2%;
      --foreground: 242 25% 100%;
      --muted: 242 25% 9%;
      --muted-foreground: 242 11% 73%;
      --popover: 242 60% 3%;
      --popover-foreground: 0 0% 100%;
      --card: 242 60% 3%;
      --card-foreground: 0 0% 100%;
      --border: 242 2% 14%;
      --input: 242 2% 14%;
      --primary: 242 70% 25%;
      --primary-foreground: 242 70% 85%;
      --secondary: 242 11% 15%;
      --secondary-foreground: 242 11% 75%;
      --accent: 242 11% 15%;
      --accent-foreground: 242 11% 75%;
      --destructive: 6 85% 48%;
      --destructive-foreground: 0 0% 100%;
      --ring: 242 70% 25%;
      --chart-1: 242 70% 25%;
      --chart-2: 242 11% 15%;
      --chart-3: 242 11% 15%;
      --chart-4: 242 11% 18%;
      --chart-5: 242 73% 25%;
    }
  }
  

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
