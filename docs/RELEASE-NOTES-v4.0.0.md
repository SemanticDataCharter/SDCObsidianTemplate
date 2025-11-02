# Release Notes: v4.0.0

**Release Date**: November 2, 2025
**Type**: Major Release (Initial Public Release)
**SDC Compatibility**: SDC4

---

## 🎉 Welcome to SDCStudio Obsidian Template v4.0.0!

This is the first public release of the SDCStudio Obsidian Template, a complete solution for creating SDC4-compliant dataset descriptions in Obsidian.

---

## ✨ Highlights

### 🚀 Revolutionary UX

- **No More Hanging!** - Template uses non-blocking prompts with visual feedback. The v1.0 freezing issue is completely solved.
- **Clear Progress** - Live document updates and progress indicators show exactly what's happening
- **Guided Workflow** - Step-by-step prompts walk you through creating complete dataset descriptions

### 🎯 User-Friendly Design

- **Simple Types** - Choose from `text`, `integer`, `decimal`, `boolean`, `date`, `datetime`, `identifier`, `email`, `url`
- **Automatic Mapping** - Your selections automatically map to the correct SDC4 XD components
- **Smart Prompts** - Only shows relevant questions based on your choices (e.g., units only for numeric types)

### 🔗 Standards Integration

- **Component Reuse** - Reference existing components with `@ProjectName:ComponentLabel` syntax
- **NIEM, FHIR, HL7v3** - Full support for referencing standards-based components
- **openEHR** - Compatible with other semantic health data standards

### 📏 Scalability

- **Start Small** - Create 2-3 columns interactively for quick setup
- **Grow Big** - Copy-paste templates for unlimited columns
- **No Limits** - Build datasets of any size without performance issues

### 🎨 Professional Styling

- **SDCStudio Colors** - Official design system (#0a2342, #2ca58d, #f0a500, #f7f9fb)
- **Beautiful Tables** - Blue headers matching SDCStudio web application
- **Safe for Upload** - CSS is display-only, doesn't modify your markdown files

---

## 🆕 What's New

### Template Features

✅ **Non-blocking prompts** with async/await pattern
✅ **User-friendly type system** with dropdown selection
✅ **Automatic SDC4 mapping** for all types
✅ **Component reuse support** (@ProjectName:ComponentLabel)
✅ **Structured constraints** in proper YAML format
✅ **Complete YAML front matter** with all metadata fields
✅ **LLM enrichment toggle** for semantic enhancement
✅ **Visual progress indicators** showing what's happening
✅ **Conditional prompts** based on type selection
✅ **Unlimited enumerations** with simple or table format
✅ **Copy-paste templates** for rapid expansion
✅ **Sub-cluster support** for hierarchical structures

### CSS Theme Features

✅ **SDCStudio design system** colors and typography
✅ **Professional table styling** with hover effects
✅ **Special dataset element styling** for columns and clusters
✅ **Display-only** - does NOT modify markdown files
✅ **WCAG AA compliant** colors and contrast
✅ **Light/dark theme support** for Obsidian
✅ **Scrollbar styling** for cohesive look
✅ **Code block formatting** matching SDCStudio

### Documentation

✅ **Complete installation guide** with troubleshooting
✅ **Detailed usage guide** with examples
✅ **Theme setup guide** with customization tips
✅ **Type reference table** for quick lookup
✅ **Component reuse examples** for standards
✅ **Contributing guidelines** for open source participation

---

## 🔧 What's Fixed

### From v1.0 (Internal)

| Problem (v1.0) | Solution (v4.0.0) |
|----------------|-------------------|
| ❌ System hanging and freezing | ✅ Non-blocking prompts with visual feedback |
| ❌ Limited to 2 columns | ✅ Unlimited scalability via copy-paste |
| ❌ Confusing type system | ✅ User-friendly dropdown with SDC4 mapping |
| ❌ No component reuse | ✅ Full @ProjectName:ComponentLabel support |
| ❌ Poor markdown structure | ✅ Spec-compliant output matching guide |
| ❌ Incomplete YAML | ✅ Complete front matter with all fields |
| ❌ Unstructured constraints | ✅ Proper YAML constraint format |
| ❌ No visual feedback | ✅ Progress indicators and live updates |
| ❌ No styling | ✅ Professional SDCStudio CSS theme |
| ❌ Poor scalability | ✅ Works for any dataset size |

---

## 📦 What's Included

### Files in This Release

```
SDCObsidianTemplate/
├── templates/
│   └── ObsidianDataSetTemplate.md    # v4.0.0 Template (16 KB)
├── snippets/
│   └── sdcstudio-theme.css           # CSS Theme (11 KB)
├── docs/
│   ├── INSTALL.md                    # Installation guide
│   ├── USAGE.md                      # Usage guide
│   ├── THEME.md                      # Theme guide
│   └── RELEASE-NOTES-v4.0.0.md      # This file
├── CHANGELOG.md                      # Version history
├── CONTRIBUTING.md                   # Contribution guidelines
├── LICENSE                           # Apache 2.0
└── README.md                         # Repository overview
```

### Download Options

1. **GitHub Release** - Download ZIP from releases page
2. **Clone Repository** - `git clone https://github.com/AxiusSDC/SDCObsidianTemplate.git`
3. **Website** - Download from [axius-sdc.github.io](https://axius-sdc.github.io)

---

## 🔄 Upgrade Guide

### New Users

Simply follow the installation guide in `docs/INSTALL.md`.

### From v1.0 (Internal Users)

1. **Backup** your old template (optional)
2. **Replace** `ObsidianDataSetTemplate.md` with v4.0.0
3. **Add** `sdcstudio-theme.css` to `.obsidian/snippets/`
4. **Enable** CSS snippet in Obsidian settings
5. **Enjoy** the improved experience!

**No migration needed** - v4.0.0 generates compatible markdown for SDCStudio.

---

## ⚙️ System Requirements

- **Obsidian**: v1.0.0 or later
- **Templater Plugin**: v1.16.0 or later (free community plugin)
- **Operating Systems**: Windows 10/11, macOS 10.15+, Linux (most distributions)
- **Disk Space**: ~70 KB installed

---

## 🎯 SDC4 Compliance

This release is **fully compliant** with SDC4 specifications:

### Type Mapping

| User Type | SDC4 XD Type | Notes |
|-----------|--------------|-------|
| `text` | XdString, XdToken | With/without enumeration |
| `integer` | XdCount, XdOrdinal, XdIdentifier | Based on units and enum |
| `decimal` | XdQuantity, XdFloat, XdDouble | Based on units |
| `boolean` | XdBoolean | True/False values |
| `date` | XdTemporal | Dates only |
| `datetime` | XdTemporal | Dates with time |
| `identifier` | XdIdentifier | IDs, codes, UUIDs |
| `email` | XdString | With format validation |
| `url` | XdLink | Web links, URIs |

### Constraint Mapping

- `required` → Cardinality (0..1 or 1..1)
- `unique` → Uniqueness constraint
- `range` → min/max values for numeric types
- `precision` → Decimal places for XdQuantity
- `format` → Regex pattern for text types

### YAML Front Matter

```yaml
template_version: "4.0.0"
creation_date: YYYY-MM-DD HH:mm:ss
last_modified: YYYY-MM-DD HH:mm:ss
dataset:
  name: "Dataset Name"
  description: "Description"
  domain: "Optional domain"
  creator: "Optional creator"
  project: "Optional project link"
enrichment:
  enable_llm: true/false
```

---

## 🔗 Integration with SDCStudio

### Workflow

```
1. Create dataset in Obsidian (this template)
   ↓
2. Upload markdown to SDCStudio
   ↓
3. SDCStudio parses with MD2PD
   ↓
4. Generate outputs (XSD, XML, JSON, RDF, SHACL, GQL)
```

### Compatibility

✅ **100% Compatible** - Markdown output works perfectly with SDCStudio v4.0.0+
✅ **MD2PD Parser** - Tested and verified with SDCStudio's parser
✅ **No CSS in Files** - Theme is display-only, doesn't affect upload
✅ **Spec-Compliant** - Follows official dataset-template.md guide exactly

---

## 📊 Performance

### Before (v1.0)

- ⏱️ **Hanging**: System would freeze for 30+ seconds
- 🐌 **Slow**: Blocking prompts one after another
- 📏 **Limited**: Only 2 columns, 1 cluster
- 😕 **UX**: Confusing and frustrating

### After (v4.0.0)

- ⚡ **Fast**: No hanging, immediate feedback
- 🚀 **Responsive**: Non-blocking prompts
- 📈 **Scalable**: Unlimited columns and clusters
- 😊 **UX**: Clear, intuitive, professional

---

## 🤝 Contributing

This is an **open source project**! We welcome:

- 🐛 **Bug reports** - Help us find and fix issues
- 💡 **Feature requests** - Suggest improvements
- 📝 **Documentation** - Improve guides and examples
- 🔧 **Code contributions** - Submit pull requests

See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines.

---

## 📞 Support

- **Documentation**: [docs/](../docs/) folder
- **Issues**: [GitHub Issues](https://github.com/AxiusSDC/SDCObsidianTemplate/issues)
- **Discussions**: [GitHub Discussions](https://github.com/AxiusSDC/SDCObsidianTemplate/discussions)
- **Website**: [axius-sdc.github.io](https://axius-sdc.github.io)

---

## 🙏 Acknowledgments

Thanks to:
- **Obsidian** team for the amazing platform
- **Templater** plugin developer for the powerful templating system
- **Semantic Data Charter** community for SDC4 specifications
- **Early testers** who provided feedback during development
- **Axius SDC** team for supporting open source

---

## 📝 License

Apache License 2.0

Copyright © 2025 Axius SDC, Inc.

See [LICENSE](../LICENSE) for full details.

---

## 🔮 What's Next?

### Planned for v4.1.0

- Auto-update checker
- Additional pre-built templates
- Enhanced validation feedback
- Dark theme optimizations
- Mobile-responsive improvements

### Long-term Vision

- Direct SDCStudio upload from Obsidian
- Template marketplace
- Community-contributed templates
- Multi-language support

---

## 🌟 Get Started

1. **Download** from [GitHub releases](https://github.com/AxiusSDC/SDCObsidianTemplate/releases/latest)
2. **Install** following [docs/INSTALL.md](INSTALL.md)
3. **Create** your first dataset description
4. **Upload** to SDCStudio
5. **Star** the repository if you find it useful! ⭐

---

**Made with ❤️ by [Axius SDC, Inc.](https://axius-sdc.github.io)**

*Empowering semantic data modeling for everyone*
