# Changelog

All notable changes to the SDCStudio Obsidian Template will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html) with SDC4 alignment.

## Version Numbering

This project follows **modified semantic versioning**:

- **MAJOR** = SDC Reference Model version (currently **4** for SDC4)
- **MINOR** = Feature releases for the artifact
- **PATCH** = Bug fixes and minor updates

All versions in the 4.x.x series are compatible with SDC4.

---

## [4.0.0] - 2025-11-02

### 🎉 Initial Public Release

Complete redesign of the Obsidian Dataset Template for SDC4-compliant dataset descriptions.

### ✨ Added

#### Template Features
- **Non-blocking prompts** with visual feedback (no more system hanging!)
- **User-friendly type system** - Select from `text`, `integer`, `decimal`, `boolean`, `date`, `datetime`, `identifier`, `email`, `url`
- **Automatic SDC4 mapping** - Types automatically map to correct XD components
- **Component reuse support** - Reference existing components with `@ProjectName:ComponentLabel` syntax
- **Structured constraints** - Proper YAML format for required, unique, range, precision, format
- **Complete YAML front matter** - All metadata fields including LLM enrichment toggle
- **Scalable design** - Create 2-3 columns interactively, unlimited via copy-paste templates
- **Progress indicators** - Live document updates show what's happening
- **Conditional prompts** - Only show relevant prompts based on type selection

#### CSS Theme Features
- **SDCStudio design system** - Official color palette (#0a2342, #2ca58d, #f0a500, #f7f9fb)
- **Professional table styling** - Blue headers matching SDCStudio web app
- **Special dataset styling** - Column and cluster headers get highlighted formatting
- **Display-only** - Does NOT modify markdown files (safe for SDCStudio upload)
- **WCAG AA compliant** - Accessible colors and contrast ratios
- **Cross-theme support** - Works with both light and dark Obsidian themes

#### Documentation
- Complete installation guide with troubleshooting
- Detailed usage guide with examples
- Theme setup and customization guide
- Type reference table
- Component reuse examples

### 🔧 Changed

#### From v1.0 (Deprecated)
- **UX**: Blocking prompts → Non-blocking with visual feedback
- **Scalability**: Limited to 2 columns → Unlimited columns
- **Type system**: Free-text prompts → Dropdown with SDC4 mapping
- **Structure**: Incorrect heading levels → Spec-compliant markdown
- **Features**: No component reuse → Full @ProjectName:ComponentLabel support
- **Constraints**: Unstructured → Proper YAML format
- **Front matter**: Incomplete → Complete with all fields

### 🐛 Fixed

- **System hanging** - Template no longer freezes or blocks Obsidian
- **Poor UX** - Clear, guided workflow with progress indicators
- **Incorrect markdown structure** - Now matches dataset-template.md guide exactly
- **Missing YAML fields** - All required front matter fields included
- **Type confusion** - Clear dropdown with descriptions and SDC4 mapping

### 📋 Technical Details

**Template:**
- File: `templates/ObsidianDataSetTemplate.md`
- Size: ~16 KB
- Lines of code: ~387
- Technology: Templater plugin syntax (`<%* ... %>`)
- Non-blocking async/await pattern with `editor.setValue()`

**CSS Theme:**
- File: `snippets/sdcstudio-theme.css`
- Size: ~11 KB
- Lines of code: ~391
- Specificity: `.markdown-preview-view` and `.cm-*` selectors
- Variables: CSS custom properties for easy customization

### 🎯 Compatibility

- **Obsidian**: v1.0.0 or later
- **Templater**: v1.16.0 or later
- **SDCStudio**: v4.0.0+
- **SDC Reference Model**: SDC4
- **Operating Systems**: Windows, Mac, Linux

### 🏗️ Repository Setup

- **License**: Apache 2.0
- **Hosting**: GitHub (AxiusSDC/SDCObsidianTemplate)
- **Documentation**: Complete guides in `docs/` folder
- **Contributing**: Guidelines for community contributions

### 📦 Distribution

- **GitHub Releases**: Source code and downloadable ZIP
- **Website**: Link from axius-sdc.github.io
- **SDCStudio**: External links for easy access

---

## [Unreleased]

### Planned for v4.1.0

#### Features Under Consideration
- [ ] Auto-update checker
- [ ] Additional pre-built templates for common use cases
- [ ] Multi-language support (i18n)
- [ ] Enhanced validation feedback
- [ ] Direct SDCStudio upload from Obsidian (via plugin)
- [ ] Template marketplace for community templates
- [ ] Dark theme optimizations
- [ ] Mobile-responsive CSS improvements

#### Community Requests
- Track feature requests in [GitHub Issues](https://github.com/AxiusSDC/SDCObsidianTemplate/issues)

---

## Version History Summary

| Version | Release Date | Key Changes |
|---------|--------------|-------------|
| 4.0.0 | 2025-11-02 | Initial public release, complete redesign |
| 1.0 (deprecated) | N/A | Internal use only, deprecated due to UX issues |

---

## Upgrade Guide

### From v1.0 to v4.0.0

Since v4.0.0 is a complete redesign, upgrading is straightforward:

1. **Backup your old template** (if desired)
2. **Replace** `ObsidianDataSetTemplate.md` with the new v4.0.0 version
3. **Add** `sdcstudio-theme.css` to `.obsidian/snippets/`
4. **Enable** CSS snippet in Obsidian settings
5. **Review** new features in usage guide

**No migration needed** - v4.0.0 generates compatible markdown for SDCStudio.

---

## Support

For questions about changes or upgrading:
- Check the [documentation](docs/)
- Open an [issue](https://github.com/AxiusSDC/SDCObsidianTemplate/issues)
- Visit [axius-sdc.github.io](https://axius-sdc.github.io)

---

## Contributing

We welcome changelog contributions! When submitting PRs, please update this file following the [Keep a Changelog](https://keepachangelog.com/) format.

---

**Legend:**
- ✨ Added
- 🔧 Changed
- 🐛 Fixed
- 🗑️ Removed
- ⚠️ Deprecated
- 🔒 Security
