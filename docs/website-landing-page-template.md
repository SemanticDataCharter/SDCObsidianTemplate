# Website Landing Page Template

This directory contains a ready-to-use HTML template for creating a landing page on your website (e.g., axius-sdc.github.io).

## File

`website-landing-page-template.html` - Complete standalone HTML page with:
- Hero section with download button
- Feature highlights
- Screenshots section (add images)
- Type reference table
- Requirements and compatibility info
- All download links point to GitHub releases

## Usage

1. **Copy the file** to your website repository
2. **Rename** to something like `resources/obsidian-template.html`
3. **Adapt styling** to match your site's theme (colors, fonts, layout)
4. **Add screenshots** to `resources/images/obsidian/` directory
5. **Update** your site's resources page to link to this new page

## Key Points

- ✅ All download links already point to GitHub releases (no local files needed)
- ✅ Links use `/releases/latest` so they always point to current version
- ✅ Includes Google Analytics tracking code (customize as needed)
- ✅ Mobile-responsive design
- ✅ SEO-optimized meta tags

## Customization

### Colors

The template uses SDCStudio colors by default:
```css
--sdc-primary: #0a2342;       /* Deep Blue */
--sdc-secondary: #2ca58d;     /* Teal */
--sdc-accent: #f0a500;        /* Gold */
--sdc-bg-light: #f7f9fb;      /* Background */
```

Change these in the CSS variables section to match your site.

### Sections

You can remove or rearrange sections:
- Hero (required)
- Stats
- Features grid
- Type reference table
- Requirements
- Compatibility
- CTA (call to action)
- Support

### Screenshots

Add images to enhance the page:
- `screenshot-1.png` - Template prompts
- `screenshot-2.png` - Styled output
- `screenshot-3.png` - Before/after comparison

See `docs/images/README.md` for screenshot guidelines.

## Integration with Your Site

### Navigation

Add to your main navigation:
```html
<nav>
    <a href="/">Home</a>
    <a href="/resources.html">Resources</a>
    <a href="/resources/obsidian-template.html">Obsidian Template</a>
</nav>
```

### Resources Page

Add a card:
```html
<div class="resource-card">
    <h3>📝 Obsidian Template</h3>
    <p>Create SDC4-compliant dataset descriptions in Obsidian</p>
    <a href="resources/obsidian-template.html">Learn More</a>
</div>
```

## Maintenance

- Links point to GitHub, so no updates needed when new versions release
- Just update version numbers in text if you want to highlight latest version
- Screenshots should be updated occasionally to reflect current UI

## Alternative: Minimal Page

If you prefer a minimal landing page, use this simpler structure:

```html
<section>
    <h1>SDCStudio Obsidian Template</h1>
    <p>Create SDC4-compliant dataset descriptions with ease</p>
    <a href="https://github.com/SemanticDataCharter/SDCObsidianTemplate/releases/latest">
        Download Latest Release
    </a>
    <a href="https://github.com/SemanticDataCharter/SDCObsidianTemplate">
        View on GitHub
    </a>
</section>
```

## Support

For questions about website integration, see the main repository or open an issue.
