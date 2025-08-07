
## Create Code: Get good code out of Figma


### Initial command

```
Create a react-native website called "Dub Merch". It is a site that showcases Professional Womens Basketball Player Merchandise. It is not an ecommerce site. It is a site that aggregates the best Merchandise from Player and other sites. 

Create a home page. 

The header area should be as follows: Include the Logo large at the top. Include the tagline in small font in the top left of the page. The tagline is "Buy from the ballers, not the suits."

The body consists of images of player merchandise. Photos should be very large and take up a significant portion of the screen. Include 3 rows of 3 photos. Photo dimensions should be close to 3:4 in landscape orientation. Every photo is a different item. The caption should include the [player name] and [item name]. The combination of player name and item name will be unique to each item. Each item should also have hashtags. The hashtags will include the team the player plays on. We may add more hashtags later. The body should have infinite scroll functionality rather than pages. Meaning if we later have 18 images, you will just scroll down to see them rather than using page navigation. 


* Use a standard react file structure with a src/ folder that contains source code, css code, figma components and imports. Also use a public folder which holds an images folder which stores images.
* Turn SGV images to Typescript files rather than keeping them as images.
* The logo to include is in the figma file. 
* The color scheme is as follows: 
- Primary Purple: #330432
- Primary Blue: #003153  
- Primary Pink: #CE7994
- Background: #fae5da
- Accent Blue: #21AAE2


Create a product item page. Each of the 9 items from the home page should have a product item page. You navigate to the product item page by clicking either the produc timage or product caption. The product item page should contain 4 images. Please use any women's basketball-related images for this. The product item page should have the Product title again and then a short description about the product. Use lorem ipsum text for now. 

Create a Guidelines.md file that I can use to update with design guidelines.


```



Usage:** Run these three prompts in sequence for the most thorough error checking and fixing of your Figma Make generated code.
###  Prompt 1: Dependencies & Configuration
```
Review the package.json and configuration files for these issues: 1) All React dependencies have compatible versions with no conflicts, 2) Include all necessary dev dependencies (Tailwind CSS, PostCSS, Autoprefixer), 3) Add any missing peer dependencies, 4) Ensure proper scripts for dev, build, and preview commands are included, 5) Verify Tailwind CSS is properly configured with PostCSS and Autoprefixer, 6) Check that Tailwind config includes all custom colors, spacing, and breakpoints used in the components, 7) Ensure all configuration files are properly set up. Ensure the correct base styles are called in the CSS file (Tailwind). Fix any issues found.
```

### Prompt 2: React Code Quality & Structure
```
Review all React components and code for these issues: 1) Missing React imports and improper component exports, 2) Invalid JSX syntax and unclosed tags, 3) Missing keys in mapped lists and arrays, 4) Improper React hooks usage (useState, useEffect) with incorrect dependencies, 5) Event handlers that aren't properly bound, 6) Unused variables and imports, 7) Props that aren't properly typed or passed correctly, 8) Console.log statements or debugging code that should be removed, 9) Missing alt attributes on images, 10) Incorrect className attributes (should be camelCase), 11) File paths and imports that are incorrect or case-sensitive mismatches, 12) Component file names that don't match their exports, 13) Improper relative vs absolute import paths. Fix all issues found.
```
### Prompt 3: Styling & Final Quality Check
```
Review all styling and perform final quality checks for these issues: 1) Invalid or misspelled Tailwind classes, 2) Incorrect responsive prefixes (sm:, md:, lg:) usage, 3) Conflicting or redundant Tailwind classes on the same element, 4) Images and assets that are improperly referenced or have invalid source paths, 5) Any remaining syntax errors like missing semicolons or brackets, 6) Accessibility issues beyond alt tags (proper semantic HTML), 7) Any hardcoded values that should use Tailwind utilities instead, 8) Ensure all custom styles are properly applied and don't conflict with Tailwind. Run a final check to ensure the app will compile and run without errors.
```



## Finish Code: Finish Figma code in Replit

### Fix folder structure

AI Command:
```
Edit the folder structure to comply with a standard React project in Replit. Ensure all references to files are correct. 
```

### Create config files

AI Command:
```
Please create required configuration files to run my app. Allow all hosts in vite.config.ts file with allowedHosts: ['all']. Ensure all required items are imported for Typescript and Vite. 
```





## Debug Replit Deploy
### Vite Configuration 
File: `vite.config.ts`

Change: 
* Allow all hosts in config file with

```
allowedHosts: [
  'all', // Allow all hosts
  '<<host text>>' // Add specific host
],
```

AI Command: 
* Allow all hosts in vite.config.ts file with allowedHosts: ['all']


#### Restart Vite server to apply changes

```
$   npm run dev
```


### CSS File Modification 
File: `src/styles/globals.css`

Change: 
* Error: @layer base was used without the @tailwind base directive. Add to the top of your globals.css file:

```
@tailwind base;
@tailwind components;
@tailwind utilities;
@layer base {
  :root {
    --background: 0 0% 100%;
    /* Other custom root variables can be added here */
  }
}
```
AI Command:

* Ensure necessary base styles are in the css file including @tailwind.


### Misc

import path from 'path' // This is for the typescript compiler
npm install --save-dev @types/node //This is for the Typescript environment
