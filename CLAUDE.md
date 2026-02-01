# Project Context

## What is this?

A personal website designed to look like it's being edited in **Microsoft FrontPage 2000**. The entire UI mimics the FrontPage editor interface - title bar, menus, toolbars, folder panel, and editor area. Your actual website content appears in the "editor" as if you're building a page in FrontPage.

## Tech Stack

- **Astro** - Static site generator
- **Plain CSS** - Windows 98/2000 styling (no Tailwind, no frameworks)
- **GitHub Pages** - Deployment target

## Design Concept

The website wraps content in a FrontPage 2000 chrome:
- Blue gradient Windows title bar
- Menu bar (File, Edit, View, Insert, Format, Tools, Table, Frames, Window, Help)
- Toolbars with emoji icons (save, print, bold, italic, etc.)
- Left sidebar: Views panel (teal) + Folder List (file tree navigation)
- Main area: White editor with content styled like a FrontPage theme
- Bottom: Normal/HTML/Preview tabs + status bar

Content uses classic FrontPage theme styling:
- Comic Sans MS for h1 headings
- Times New Roman for body text
- Teal (#006666) for main headings
- Dark red (#990000) for h2 subheadings
- Blue underlined links

## File Structure

```
src/
├── layouts/
│   └── Layout.astro      # Main FrontPage UI wrapper
├── pages/
│   ├── index.astro       # Home page
│   ├── about.astro       # About page
│   ├── articles/         # Article pages
│   │   ├── index.astro
│   │   ├── why-flash-was-great.astro
│   │   ├── retro-web-design.astro
│   │   └── css-animations-guide.astro
│   └── notes/            # Note pages
│       ├── index.astro
│       ├── gsap-quick-tips.astro
│       ├── terminal-aliases.astro
│       ├── color-palette-generator.astro
│       └── web-audio-basics.astro
└── styles/
    └── global.css        # All Windows 98/FrontPage styling
```

## Key Files

- **`src/layouts/Layout.astro`** - The FrontPage UI shell. Takes `title` and `filename` props. The filename appears in the title bar and editor header.
- **`src/styles/global.css`** - All the Windows 98 styling (beveled borders, colors, toolbars, etc.)

## Adding New Pages

1. Create a new `.astro` file in the appropriate folder
2. Use the Layout component with title and filename:
   ```astro
   ---
   import Layout from '../layouts/Layout.astro';
   const base = import.meta.env.BASE_URL;
   ---
   <Layout title="Page Title" filename="mypage.htm">
     <h1>Page Title</h1>
     <p>Content here...</p>
   </Layout>
   ```
3. Add the page to the folder tree in `Layout.astro` (around line 150-230)

## Running Locally

```bash
npm install
npm run dev
```

## Deployment

Configured for GitHub Pages via `.github/workflows/deploy.yml`. Deploys on push to `main`.

Site URL: `https://fjaguero.github.io/website/`

## Style Guidelines

- Use semantic HTML (h1, h2, p, ul, hr)
- The CSS in global.css handles all FrontPage theme styling
- Use `<hr />` for visual separation (renders as gradient line)
- Use `.fp-nav-bar` and `.fp-nav-btn` for navigation buttons
- Use `.back-link` class for "← Back to X" links
- Escape curly braces in code blocks with `&#123;` and `&#125;`

## Ideas for Future

- Make toolbar buttons functional (e.g., toggle between Normal/HTML views)
- Add a fake "Save" dialog popup
- Implement collapsible folder tree
- Add more FrontPage themes (Expedition, Capsules, etc.)
- "Publish Web" animation
- Fake loading/saving status messages
