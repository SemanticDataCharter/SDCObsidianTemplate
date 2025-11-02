# SDCStudio Obsidian Template

[![Version](https://img.shields.io/badge/version-4.0.0-blue.svg)](https://github.com/AxiusSDC/SDCObsidianTemplate/releases)
[![License](https://img.shields.io/badge/license-Apache%202.0-green.svg)](LICENSE)
[![SDC](https://img.shields.io/badge/SDC-4.0-orange.svg)](https://github.com/SemanticDataCharter)

**Create SDC4-compliant dataset descriptions with ease using Obsidian**

An interactive [Templater](https://github.com/SilentVoid13/Templater) template and professional CSS theme for creating [SDC4](https://github.com/SemanticDataCharter) (Semantic Data Charter) compliant dataset descriptions in [Obsidian](https://obsidian.md).

---

## 🚀 Quick Start

1. **Install Prerequisites**
   - [Obsidian](https://obsidian.md) v1.0.0+
   - [Templater Plugin](https://github.com/SilentVoid13/Templater) v1.16.0+ (free community plugin)

2. **Download Template**
   - [Download latest release](https://github.com/AxiusSDC/SDCObsidianTemplate/releases/latest)
   - Or clone this repository

3. **Install**
   - Copy `templates/ObsidianDataSetTemplate.md` to your vault's `templates/` folder
   - Copy `snippets/sdcstudio-theme.css` to your vault's `.obsidian/snippets/` folder
   - Enable CSS snippet in Obsidian Settings → Appearance → CSS Snippets

4. **Use**
   - Create new note in Obsidian
   - Run Templater: Insert template → ObsidianDataSetTemplate
   - Follow the interactive prompts
   - Upload resulting markdown to [SDCStudio](https://github.com/AxiusSDC/SDCStudio)

📚 **[Full Installation Guide](docs/INSTALL.md)** | 📖 **[Usage Guide](docs/USAGE.md)** | 🎨 **[Theme Guide](docs/THEME.md)**

---

## ✨ Features

### Interactive Template (v4.0.0)

- ✅ **Non-blocking prompts** - No more system hanging!
- ✅ **User-friendly type system** - Select from `text`, `integer`, `decimal`, `boolean`, `date`, `datetime`, `identifier`, `email`, `url` with automatic SDC4 mapping
- ✅ **Component reuse** - Reference existing components from NIEM, FHIR, HL7v3, openEHR with `@ProjectName:ComponentLabel` syntax
- ✅ **Structured constraints** - Proper YAML format for required, unique, range, precision, format constraints
- ✅ **Scalable** - Create 2-3 columns interactively, unlimited via copy-paste templates
- ✅ **Complete YAML front matter** - All metadata fields including LLM enrichment toggle
- ✅ **Visual feedback** - Progress indicators show what's happening

### Professional Theme

- ✅ **SDCStudio colors** - Official design system (#0a2342, #2ca58d, #f0a500, #f7f9fb)
- ✅ **Professional tables** - Blue headers matching SDCStudio web app
- ✅ **Special styling** - Dataset columns and clusters get highlighted formatting
- ✅ **Display-only** - Does NOT modify your markdown files (safe for SDCStudio upload)
- ✅ **WCAG compliant** - Accessible colors and contrast ratios

---

## 📦 What's Included

```
SDCObsidianTemplate/
├── templates/
│   └── ObsidianDataSetTemplate.md    # Main Templater template (v4.0.0)
├── snippets/
│   └── sdcstudio-theme.css           # CSS theme for SDCStudio styling
├── docs/
│   ├── INSTALL.md                    # Installation guide
│   ├── USAGE.md                      # Usage guide with examples
│   └── THEME.md                      # Theme customization guide
├── LICENSE                           # Apache 2.0
└── README.md                         # This file
```

---

## 💡 Example Usage

### Type Reference

| Type You Write | Maps To SDC4 | When to Use |
|----------------|--------------|-------------|
| `text` | XdString, XdToken | Free text, strings, categorical with enum |
| `integer` | XdCount, XdOrdinal, XdIdentifier | Whole numbers (add units for XdCount) |
| `decimal` | XdQuantity, XdFloat, XdDouble | Decimals (add units for XdQuantity) |
| `boolean` | XdBoolean | True/False, Yes/No |
| `date` | XdTemporal | Dates only (YYYY-MM-DD) |
| `datetime` | XdTemporal | Dates with time |
| `identifier` | XdIdentifier | IDs, codes, UUIDs |
| `email` | XdString (validated) | Email addresses |
| `url` | XdLink | Web links, URLs, URIs |

### Component Reuse

```markdown
### Column: State
**ReuseComponent**: @NIEM:StateUSPostalServiceCode
**Type**: text
**Description**: US State postal code

### Column: PatientID
**ReuseComponent**: @HL7v3:PatientIdentifier
**Type**: identifier
**Description**: Unique patient identifier
```

---

## 🔄 Version History

### v4.0.0 (2025-11-02) - Current

**Major redesign fixing all v1.0 issues**

**Fixed**:
- ❌ System hanging → ✅ Non-blocking prompts with visual feedback
- ❌ Limited to 2 columns → ✅ Unlimited scalability
- ❌ Confusing UX → ✅ Clear, guided workflow
- ❌ No component reuse → ✅ Full @ProjectName:ComponentLabel support
- ❌ Poor markdown structure → ✅ Spec-compliant output

**New Features**:
- Component reuse from NIEM, FHIR, HL7v3, openEHR
- User-friendly type system with SDC4 mapping
- Complete YAML front matter
- Structured constraints (YAML format)
- LLM enrichment toggle
- Copy-paste templates for scalability
- SDCStudio design system theme

**Breaking Changes**: None (new major version)

[Full Changelog](CHANGELOG.md)

---

## 🛠️ Installation

### Quick Install

1. **Copy template file**:
   ```bash
   cp templates/ObsidianDataSetTemplate.md [your-vault]/templates/
   ```

2. **Copy CSS theme**:
   ```bash
   cp snippets/sdcstudio-theme.css [your-vault]/.obsidian/snippets/
   ```

3. **Configure Templater**:
   - Obsidian Settings → Templater
   - Set "Template folder location" to `templates`

4. **Enable CSS theme**:
   - Obsidian Settings → Appearance → CSS Snippets
   - Toggle ON "sdcstudio-theme"

📚 **[Detailed Installation Guide](docs/INSTALL.md)**

---

## 📖 Documentation

- **[Installation Guide](docs/INSTALL.md)** - Step-by-step setup instructions
- **[Usage Guide](docs/USAGE.md)** - How to use the template with examples
- **[Theme Guide](docs/THEME.md)** - CSS theme setup and customization
- **[Changelog](CHANGELOG.md)** - Version history and changes
- **[Contributing](CONTRIBUTING.md)** - How to contribute to this project

---

## 🤝 Contributing

We welcome contributions! This project is part of [Axius SDC, Inc.'s](https://axius-sdc.github.io) commitment to open source.

**Ways to contribute**:
- 🐛 Report bugs via [GitHub Issues](https://github.com/AxiusSDC/SDCObsidianTemplate/issues)
- 💡 Suggest features or improvements
- 📝 Improve documentation
- 🔧 Submit pull requests

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## 🏢 About

### Project Information

- **Maintained by**: [Axius SDC, Inc.](https://axius-sdc.github.io)
- **Part of**: [Semantic Data Charter](https://github.com/SemanticDataCharter) ecosystem
- **Works with**: [SDCStudio](https://github.com/AxiusSDC/SDCStudio) v4.0.0+
- **License**: Apache 2.0 (see [LICENSE](LICENSE))

### Related Projects

- **[SDCStudio](https://github.com/AxiusSDC/SDCStudio)** - Django application for creating SDC4 data models
- **[Semantic Data Charter](https://github.com/SemanticDataCharter)** - Core SDC4 reference model
- **[Axius SDC Website](https://axius-sdc.github.io)** - Company website and resources

---

## 📊 Use Cases

Perfect for:

- 📊 **Data Architects** - Building SDC4-compliant schemas
- 🔬 **Researchers** - Documenting research datasets
- 🏥 **Healthcare Teams** - Creating clinical data models
- 💼 **Enterprise Teams** - Standardizing data documentation
- 🎓 **Students** - Learning semantic data modeling

---

## 🔗 Workflow

```
1. Create note in Obsidian
   ↓
2. Insert SDCStudio template
   ↓
3. Answer interactive prompts
   ↓
4. Review with beautiful styling
   ↓
5. Upload markdown to SDCStudio
   ↓
6. Generate XSD, XML, JSON, RDF, SHACL, GQL
```

---

## ⚙️ System Requirements

- **Obsidian**: v1.0.0 or later
- **Templater Plugin**: v1.16.0 or later (free)
- **Operating Systems**: Windows, Mac, Linux
- **Disk Space**: ~70 KB

---

## 🔒 Security & Privacy

- ✅ **No telemetry** - Template runs entirely locally
- ✅ **No network calls** - All processing in Obsidian
- ✅ **No data collection** - Your notes stay private
- ✅ **Open source** - Review the code yourself

---

## 📝 License

Copyright © 2025 Axius SDC, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

See [LICENSE](LICENSE) for full details.

---

## 🙏 Acknowledgments

- [Obsidian](https://obsidian.md) - For the amazing knowledge management platform
- [Templater](https://github.com/SilentVoid13/Templater) - For the powerful template plugin
- [Semantic Data Charter](https://github.com/SemanticDataCharter) - For the SDC4 reference model
- All contributors and users who provide feedback and improvements

---

## 📞 Support

- **Documentation**: Check the [docs/](docs/) folder
- **Issues**: [GitHub Issues](https://github.com/AxiusSDC/SDCObsidianTemplate/issues)
- **Discussions**: [GitHub Discussions](https://github.com/AxiusSDC/SDCObsidianTemplate/discussions)
- **Website**: [axius-sdc.github.io](https://axius-sdc.github.io)

---

## 🌟 Star This Repository

If you find this project useful, please consider giving it a ⭐️ on GitHub!

---

**Made with ❤️ by [Axius SDC, Inc.](https://axius-sdc.github.io)**

*Empowering semantic data modeling for everyone*
