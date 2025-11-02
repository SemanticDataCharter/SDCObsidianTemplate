# SDCStudio Obsidian Template v4.0.0 - Installation Guide

## What's Included

This package provides everything you need to create SDC4-compliant dataset descriptions in Obsidian:

- **Dataset Template** - Interactive Templater template for building dataset descriptions
- **SDCStudio Theme** - CSS styling that matches SDCStudio's design system
- **Documentation** - Complete usage guides for both components

## Prerequisites

Before installing, make sure you have:

1. **Obsidian** - Download from [obsidian.md](https://obsidian.md)
2. **Templater Plugin** - Install from Obsidian Community Plugins:
   - Settings → Community Plugins → Browse
   - Search for "Templater"
   - Install and Enable

## Installation Steps

### Step 1: Locate Your Obsidian Vault

First, you need to find where your Obsidian vault is stored:

1. Open Obsidian
2. Open Settings (gear icon)
3. Go to "About" section
4. Note the "Vault location" path

**Common locations:**
- Windows: `C:\Users\YourName\Documents\MyVault`
- Mac: `/Users/YourName/Documents/MyVault`
- Linux: `/home/yourname/Documents/MyVault`

### Step 2: Install the Dataset Template

1. **Create templates folder** (if it doesn't exist):
   - In your vault folder, create a folder named `templates`
   - Full path: `[your-vault]/templates/`

2. **Copy template files**:
   - Copy `ObsidianDataSetTemplate.md` from this package's `templates/` folder
   - Paste into your vault's `templates/` folder
   - Copy `README-ObsidianTemplate.md` as well (for reference)

3. **Configure Templater**:
   - Open Obsidian Settings
   - Go to Templater settings
   - Set "Template folder location" to `templates`
   - Enable "Trigger Templater on new file creation" (optional)

### Step 3: Install the SDCStudio Theme

1. **Create snippets folder** (if it doesn't exist):
   - In your vault folder, find or create `.obsidian/snippets/`
   - Note: `.obsidian` is a hidden folder
   - Full path: `[your-vault]/.obsidian/snippets/`

**Finding hidden folders:**
- **Windows**: In File Explorer, View → Show → Hidden items
- **Mac**: In Finder, press `Cmd + Shift + .` to show hidden files
- **Linux**: In file manager, View → Show Hidden Files (or press `Ctrl + H`)

2. **Copy CSS files**:
   - Copy `sdcstudio-theme.css` from this package's `snippets/` folder
   - Paste into your vault's `.obsidian/snippets/` folder
   - Copy `README-SDCStudio-Theme.md` as well (for reference)

3. **Enable the theme**:
   - Open Obsidian Settings
   - Go to "Appearance" section
   - Scroll down to "CSS snippets"
   - Click the reload icon (⟳) if "sdcstudio-theme" doesn't appear
   - Toggle ON the "sdcstudio-theme" switch

## Verification

### Test the Template

1. Create a new note in Obsidian
2. Open Command Palette (`Ctrl/Cmd + P`)
3. Search for "Templater: Insert template"
4. Select "ObsidianDataSetTemplate"
5. Follow the prompts to create a dataset description

### Test the Theme

1. Open any markdown note (or the one you just created)
2. Check that:
   - Headings are deep blue (#0a2342)
   - Links are teal (#2ca58d)
   - Tables have blue headers
   - Background is off-white (#f7f9fb)

If you don't see the styling:
- Make sure the CSS snippet is toggled ON in Settings → Appearance → CSS Snippets
- Try closing and reopening Obsidian
- Check that you're using Obsidian's light theme (Settings → Appearance → Base color scheme)

## Directory Structure After Installation

Your Obsidian vault should look like this:

```
[your-vault]/
├── .obsidian/
│   ├── snippets/
│   │   ├── sdcstudio-theme.css           ← Theme CSS
│   │   └── README-SDCStudio-Theme.md     ← Theme documentation
│   └── ... (other Obsidian files)
├── templates/
│   ├── ObsidianDataSetTemplate.md        ← Main template
│   └── README-ObsidianTemplate.md        ← Template documentation
└── ... (your notes)
```

## Usage

### Creating a New Dataset Description

1. **Create a new note** with a descriptive name (e.g., "Customer Orders Dataset")
2. **Trigger the template**:
   - Command Palette (`Ctrl/Cmd + P`)
   - Search "Templater: Insert template"
   - Select "ObsidianDataSetTemplate"
3. **Answer the prompts**:
   - Dataset metadata (name, description, domain, etc.)
   - Root cluster details
   - Create 2-3 columns interactively
   - Add sub-clusters if needed
4. **Expand as needed**:
   - Use the copy-paste templates at the bottom for more columns
   - Edit and refine the generated content

### Uploading to SDCStudio

Once your dataset description is complete:

1. Save the markdown file
2. In SDCStudio, go to Upload section
3. Select "Markdown" as input type
4. Upload your `.md` file
5. SDCStudio will parse and create an SDC4 data model

**Important**: The CSS theme only affects how Obsidian displays the markdown. Your actual `.md` file contains pure markdown with no CSS, so it will work perfectly with SDCStudio's MD2PD parser.

## Troubleshooting

### Template doesn't appear in Templater menu

**Solution**:
- Verify template is in correct folder: `[vault]/templates/`
- Check Templater settings: Settings → Templater → Template folder location
- Try restarting Obsidian

### Template prompts don't appear

**Solution**:
- Make sure you're in edit mode (not preview)
- Try creating a new note first, then run template
- Check that Templater plugin is enabled: Settings → Community plugins

### Template freezes or hangs

**Solution**:
- This should not happen with v4.0.0! The old version had this issue.
- If it does occur, try:
  - Closing and reopening Obsidian
  - Disabling other plugins temporarily
  - Checking if your computer is low on resources

### CSS theme not showing

**Solution**:
- Verify CSS file is in: `[vault]/.obsidian/snippets/`
- Check that snippet is toggled ON: Settings → Appearance → CSS Snippets
- Click reload icon (⟳) in CSS Snippets section
- Make sure you're using light theme: Settings → Appearance → Base color scheme → Light

### CSS theme affects wrong elements

**Solution**:
- The theme is designed for dataset descriptions using the template structure
- If styling other notes, you can:
  - Toggle OFF the snippet when not working with datasets
  - Customize the CSS to be more specific (edit `sdcstudio-theme.css`)

## Customization

### Changing Theme Colors

Edit `.obsidian/snippets/sdcstudio-theme.css` and modify the CSS variables at the top:

```css
:root {
    --sdc-primary: #0a2342;       /* Deep Blue */
    --sdc-secondary: #2ca58d;     /* Teal */
    --sdc-accent: #f0a500;        /* Gold */
    --sdc-bg-light: #f7f9fb;      /* Background */
}
```

Changes take effect immediately in Obsidian!

### Modifying the Template

Edit `templates/ObsidianDataSetTemplate.md` to:
- Add/remove prompts
- Change default values
- Modify the generated markdown structure

**Caution**: The template uses JavaScript syntax (`<%* ... %>`). Be careful when editing if you're not familiar with JavaScript.

## Support and Documentation

- **Template Usage Guide**: See `templates/README-ObsidianTemplate.md`
- **Theme Setup Guide**: See `snippets/README-SDCStudio-Theme.md`
- **SDCStudio Documentation**: `/home/twcook/GitHub/SDCStudio/docs/templates/dataset-template.md`
- **Issues**: Contact the SDCStudio team

## Version Information

- **Template Version**: 4.0.0
- **Theme Version**: 4.0.0
- **Release Date**: 2025-11-02
- **SDC Reference Model**: SDC4
- **Obsidian Compatibility**: v1.0.0+
- **Templater Compatibility**: v1.16.0+

## What's New in v4.0.0

### Template Improvements
- ✅ No more hanging! Non-blocking prompts with visual feedback
- ✅ Scalable: Create 2-3 columns interactively, unlimited via copy-paste
- ✅ Component reuse support (@ProjectName:ComponentLabel)
- ✅ User-friendly type system with SDC4 mapping
- ✅ Complete YAML front matter
- ✅ Structured constraints in proper format
- ✅ Professional markdown output

### Theme Features
- ✅ SDCStudio color palette (#0a2342, #2ca58d, #f0a500, #f7f9fb)
- ✅ Professional table styling with blue headers
- ✅ Special styling for dataset columns and clusters
- ✅ Teal links, blue headings
- ✅ Display-only (doesn't modify markdown files)

---

**Enjoy creating beautiful, SDC4-compliant dataset descriptions!** 🎉
