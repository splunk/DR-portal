# Copilot Instructions for DR-Portal

## Project Overview
This is the Digital Resilience (DR) Portal, a web-based hub showcasing Cisco + Splunk integration capabilities across different domains:
- Business Intelligence
- Security
- Observability
- AI/ML
- Platform Services

## Architecture
- Single-page static HTML structure with content sections for each domain
- Each domain has multiple sub-pages (e.g., ai1.html, ai2.html) for detailed demos
- Common UI components:
  - Navigation between pages via cards and back buttons
  - Consistent header with Cisco + Splunk branding
  - Corner icons specific to each section
  - Embedded iframes for interactive demos
  - Responsive design with mobile breakpoints

## File Structure
- `index.html` - Main landing page and navigation hub
- Domain-specific files:
  - `{domain}.html` - Main page for each domain (e.g., ai.html)
  - `{domain}[1-4].html` - Sub-pages with specific demos
- Assets loaded from GitHub repo URLs:
  - Background: `PortalBG.jpeg`
  - Logos: `Cisco logo blue.png`, `Splunklogo.png`
  - Icons: `{domain}thumb2.png`
  - Demo previews: `*.png`

## Styling Conventions
- CSS Variables:
  ```css
  :root {
    --o: #ffb300;  /* Orange */
    --p: #f72ea7;  /* Pink */
    --v: #7e57c2;  /* Violet */
    --text: #fff;
  }
  ```
- Font: Lexend (weights: 400, 600, 700, 800)
- Common components use consistent classes:
  - `.wrap` - Main content container
  - `.grad` - Gradient text effect
  - `.back` - Back navigation button
  - `.corner-img` - Section-specific corner icon
  - `.frame` - Demo iframe container

## Accessibility
- ARIA landmarks and labels used throughout
- Skip link available for keyboard navigation
- Interactive elements properly labeled
- Semantic HTML structure (header, main, section, etc.)
- Responsive design accommodates various devices

## Best Practices
- Keep HTML structure consistent with existing pages
- Maintain accessibility features when adding content
- Use the established CSS variable system for colors
- Load external assets from the GitHub repo URLs
- Ensure responsive design works at mobile breakpoints
- Include proper ARIA attributes for new components

## Common Patterns
- Page structure:
  ```html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <!-- Meta + title + font + styles -->
    </head>
    <body>
      <a class="back" href="index.html">←</a>
      <img class="corner-img" src="...">
      <div class="wrap" role="main">
        <!-- Content -->
      </div>
    </body>
  </html>
  ```
- Navigation cards:
  ```html
  <article class="card">
    <h3>Title</h3>
    <a class="shot" href="..." target="_self">
      <img src="..." alt="...">
    </a>
  </article>
  ```

## Integration Points
- Demo iframes loaded from cisco-full-stack-observability.navattic.com
- Assets served from github.com/splunk/DR-portal
- Font loading from fonts.googleapis.com