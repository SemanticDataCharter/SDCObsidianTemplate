# SDCStudio Obsidian Template v4.0.0 - Usage Guide

## What Changed

The Obsidian Dataset Template has been completely redesigned to fix UX/performance issues and add missing features.

### Problems Fixed ✅

1. **No More Hanging!** - Template no longer freezes or hangs your computer
   - Uses hybrid approach: collect basics first, then interactive building
   - Live document updates show progress
   - Visual progress indicators (⚙️ messages)

2. **Better UX** - Much clearer and easier to use
   - Type selection with dropdown menus showing SDC4 mapping
   - Conditional prompts (only ask for units if numeric type)
   - Clear progress tracking

3. **Scalability** - No longer limited to 2 columns
   - Create 2-3 columns interactively
   - Easy copy-paste templates for unlimited columns
   - Works for any dataset size

4. **Professional Output** - Matches dataset-template.md guide exactly
   - Correct markdown structure (### for columns, not ##)
   - Proper YAML front matter with all fields
   - Structured constraints in YAML list format

### New Features ⭐

1. **Component Reuse** - Reference existing components
   - `@NIEM:StateUSPostalServiceCode` syntax
   - Optional per column
   - Great for standards compliance (NIEM, FHIR, HL7v3)

2. **User-Friendly Types** - No more SDC4 jargon
   - `text`, `integer`, `decimal`, `boolean`, `date`, `datetime`, `identifier`, `email`, `url`
   - Shows what each type maps to in SDC4
   - Clear descriptions

3. **Complete YAML Front Matter**
   - `template_version: "4.0.0"`
   - `dataset` with name, description, domain, creator, project
   - `enrichment.enable_llm` toggle for AI semantic enrichment

4. **Structured Constraints**
   - Proper YAML format
   - `required`, `unique`, `range`, `precision`, `format`
   - Business rules field

5. **Unlimited Enumerations**
   - Simple list format (default)
   - Table format (optional)
   - Add as many values as needed

## How to Use

### First Time Setup

1. **Open Obsidian** with Templater plugin enabled
2. **Create a new note** (this will be your dataset description)
3. **Trigger the template**:
   - Command palette (Ctrl/Cmd+P)
   - Search for "Templater: Insert template"
   - Select "ObsidianDataSetTemplate"

### Interactive Flow

The template will guide you through:

#### Phase 1: Dataset Metadata (6-8 prompts)
- Dataset name (auto-filled from file name)
- Description
- Domain (optional: Healthcare, Finance, etc.)
- Creator (optional)
- Project link (optional: to link to existing project)
- LLM enrichment toggle
- Purpose, Business context
- Source, Frequency, Scope (all optional)

#### Phase 2: Root Cluster (2-3 prompts)
- Cluster name
- Description
- Purpose (optional)

#### Phase 3: First Column (7-12 prompts depending on choices)
- Column name
- Component reuse? (yes/no)
  - If yes: `@ProjectName:ComponentLabel`
- Type selection (dropdown with SDC4 mapping)
- Description
- Units (if numeric type)
- Constraints (required, unique, range, precision, format)
- Business rules (optional)
- Examples
- Enumeration? (yes/no)
  - If yes: Add unlimited values

#### Phase 4: Additional Columns (optional)
- "Add another column?" → Creates 2nd column
- "Add third column?" → Creates 3rd column
- For more: Use copy-paste templates at bottom

#### Phase 5: Sub-Cluster (optional)
- "Add a sub-cluster?" (yes/no)
- If yes: Cluster details + 1 column
- For more columns: Use copy-paste templates

### Adding More Columns Manually

At the bottom of the generated document, you'll find copy-paste templates:

```markdown
### Column: [column_name]
**Type**: text
**Description**: [Detailed description]
**Units**: [units if applicable]
**ReuseComponent**: @ProjectName:ComponentLabel [if reusing]
**Constraints**:
  - required: true|false
  - unique: true [if applicable]
  - range: [min, max] [for numeric types]
  - precision: N [for decimals]
  - format: "pattern" [for text/email]
**Business Rules**: [Optional validation rules]
**Examples**: example1, example2, example3

**Enumeration**: [If has fixed values]
  - value1: Description 1
  - value2: Description 2
```

Just copy this, fill in the details, and paste where needed!

## Type Reference

| Type You Write | Maps To SDC4 | When to Use |
|----------------|--------------|-------------|
| `text` | XdString or XdToken | Free text, strings, categorical with enum |
| `integer` | XdCount, XdOrdinal, XdIdentifier | Whole numbers (add units for XdCount) |
| `decimal` | XdQuantity, XdFloat, XdDouble | Numbers with decimals (add units for XdQuantity) |
| `boolean` | XdBoolean | True/False, Yes/No |
| `date` | XdTemporal | Dates only (YYYY-MM-DD) |
| `datetime` | XdTemporal | Dates with time |
| `identifier` | XdIdentifier | IDs, codes, UUIDs, reference numbers |
| `email` | XdString | Email addresses (validated) |
| `url` | XdLink | Web links, URLs, URIs |

## Keyword Reference

For complete documentation on all available keywords, syntax, examples, and best practices, see **[KEYWORD_REFERENCE.md](KEYWORD_REFERENCE.md)**.

This comprehensive guide covers:
- All valid column-level keywords (Type, Description, Units, Enumeration, etc.)
- Cluster-level and dataset-level keywords
- Documentation keywords for rich metadata
- Type mapping reference
- Common patterns and examples
- Validation messages and troubleshooting

## Tips

### Performance
- Template runs **much faster** than old version
- No more computer hanging!
- Progress indicators show what's happening

### Scalability
- Create 2-3 columns interactively for quick setup
- For large datasets (10+ columns): create 2-3, then copy-paste template
- Much faster than answering 100+ prompts!

### Component Reuse Examples
```markdown
### Column: State
**ReuseComponent**: @NIEM:StateUSPostalServiceCode
**Description**: US State postal code

### Column: PatientID
**ReuseComponent**: @HL7v3:PatientIdentifier
**Description**: Unique patient identifier

### Column: Diagnosis
**ReuseComponent**: @FHIR:Condition
**Description**: Primary diagnosis code
```

### Intelligent Defaults
The template suggests appropriate types based on column names:
- `customer_id`, `order_id` → suggests `identifier`
- `is_active`, `has_permissions` → suggests `boolean`
- `created_date`, `updated_at` → suggests `datetime`

## Troubleshooting

### Template won't insert
- Make sure Templater plugin is installed and enabled
- Check that template is in correct folder: `templates/`
- Try restarting Obsidian

### Prompts not appearing
- Make sure you're in edit mode (not preview)
- Try creating a new note first

### Want to skip optional prompts
- For optional prompts, leave blank or press Cancel
- Template handles empty values gracefully

### Need to start over
- Just delete the note and create a new one
- Or manually delete the content and re-run template

## Backup

The old template was backed up to:
```
/home/twcook/obsidian/templates/ObsidianDataSetTemplate.md.backup
```

If you need to revert, just rename the backup file.

## Version History

**v4.0.0** (Current)
- ✅ Complete redesign for UX and performance
- ✅ Non-blocking prompts with visual feedback
- ✅ Component reuse support
- ✅ User-friendly type system
- ✅ Structured constraints
- ✅ Complete YAML front matter
- ✅ Copy-paste templates for scalability

**v1.0** (Deprecated)
- ❌ Blocking prompts caused hanging
- ❌ Limited to 2 columns, 1 cluster
- ❌ Confusing type system
- ❌ Poor markdown structure
- ❌ No component reuse

## Support

For questions or issues:
1. Check the inline help in the generated document
2. Refer to `/home/twcook/GitHub/SDCStudio/docs/templates/dataset-template.md`
3. Contact the SDCStudio team

Enjoy the much-improved template! 🎉
