# SDCStudio Theme for Obsidian - Setup Guide

## ✅ Installation Complete!

The `sdcstudio-theme.css` file has been created in your Obsidian snippets folder.

## 🎨 How to Enable

1. **Open Obsidian**
2. **Go to Settings** (gear icon in sidebar)
3. **Appearance** section (left sidebar)
4. **Scroll to "CSS Snippets"**
5. **Click the reload icon** (⟳) if "sdcstudio-theme" doesn't appear
6. **Toggle ON** the "sdcstudio-theme" switch

That's it! Your markdown will instantly look like SDCStudio.

## 🔍 What You'll See

### Before (Default Obsidian)
- Gray headings
- Purple/blue links
- Plain tables
- Generic colors

### After (SDCStudio Theme)
- **Deep blue headings** (#0a2342)
- **Teal links** (#2ca58d)
- **Professional tables** with blue headers
- **SDCStudio color palette** throughout
- **Off-white background** (#f7f9fb)

## 📝 Important Notes

### ✅ Safe for SDCStudio Upload
- **Does NOT modify your markdown files**
- **Only changes how Obsidian displays them**
- **MD2PD parser sees pure markdown**
- **No CSS in uploaded files**

### ✅ Compatible With
- Dataset template v4.0.0 (just created)
- All existing markdown files
- Light theme (recommended)
- Dark theme (basic support)

### ✅ Special Features
- **Column headers** get blue underline
- **Cluster headers** get shaded background
- **Tables** use SDCStudio blue headers
- **Links** use SDCStudio teal
- **Code blocks** styled like SDCStudio

## 🎯 Perfect For

- Creating dataset descriptions
- Reviewing generated templates
- Documentation that will upload to SDCStudio
- Matching SDCStudio's professional look

## 🔧 Customization

If you want to tweak colors, edit `/home/twcook/obsidian/.obsidian/snippets/sdcstudio-theme.css`

Key variables at the top:
```css
--sdc-primary: #0a2342;       /* Deep Blue */
--sdc-secondary: #2ca58d;     /* Teal */
--sdc-accent: #f0a500;        /* Gold */
--sdc-bg-light: #f7f9fb;      /* Background */
```

Changes auto-reload in Obsidian!

## 💡 Tips

1. **Use light theme** for best results (SDCStudio colors designed for light)
2. **Test with a dataset** - create one with the new template to see it in action
3. **Toggle ON/OFF** anytime via Settings > Appearance > CSS Snippets
4. **No risk** - can disable instantly if you don't like it

## 🐛 Troubleshooting

**Snippet doesn't appear:**
- Click the reload icon (⟳) in CSS Snippets section
- Make sure file is in correct folder: `.obsidian/snippets/`

**Colors not showing:**
- Make sure toggle is ON (blue/green color)
- Try closing and reopening Obsidian
- Check you're using Obsidian's light theme

**Want to go back:**
- Just toggle OFF the snippet
- Everything returns to default Obsidian styling

## 📚 Reference

**SDCStudio Design System:**
- Primary: #0a2342 (Deep Blue)
- Secondary: #2ca58d (Teal)
- Accent: #f0a500 (Gold)
- Background: #f7f9fb (Off-White)
- Text: #333333 (Dark Gray)

**Font:** Inter (sans-serif), same as SDCStudio web app

**Principles:**
- Professional, accessible (WCAG AA compliant)
- Clean, data-focused design
- Consistent with SDCStudio brand

---

Enjoy your beautifully styled Obsidian workspace! 🎉
