# MD2PD Template Keyword Reference

## Quick Start

MD2PD templates use **bold keywords** followed by colons (`**Keyword**:`) to structure data. This reference lists all valid keywords and their usage.

## Template Structure

```yaml
---
template_version: "4.0.0"
dataset:
  name: "Dataset Name"
  description: "Brief description"
  creator: "Your Name"
  project: "project_ct_id"
enrichment:
  enable_llm: true
---

# Dataset Overview

[Description]

**Purpose**: Why this dataset exists
**Business Context**: How it's used

## Root Cluster: Cluster Name

[Description]

**Purpose**: What this cluster represents
**Business Context**: Business value

### Column: column_name
**Type**: text
**Description**: Detailed description
[... other keywords ...]
```

## Column-Level Keywords

These keywords are used within `### Column:` sections.

### Core Keywords (Parsed by System)

| Keyword | Required | Description | Example |
|---------|----------|-------------|---------|
| `**Type**:` | Yes | Data type (see Type Reference below) | `**Type**: text` |
| `**Description**:` | Yes | Detailed column description | `**Description**: Customer unique identifier` |
| `**Units**:` | For quantities | Measurement units | `**Units**: years` |
| `**Examples**:` | Recommended | Sample values | `**Examples**: 25, 42, 67` |
| `**Enumeration**:` | For categorical | Allowed values (see below) | See Enumeration section |
| `**Constraints**:` | Optional | Validation rules (see below) | See Constraints section |
| `**Business Rules**:` | Optional | Business logic | `**Business Rules**: Must be 18+` |
| `**Relationships**:` | Optional | Related columns | `**Relationships**: Links to orders.customer_id` |
| `**Semantic Links**:` | Optional | Ontology URIs | See Semantic Links section |
| `**Reuse**:` | Optional | Component CT_ID to reuse | `**Reuse**: ct_abc123` |
| `**ReuseComponent**:` | Optional | Component reference | `**ReuseComponent**: @NIEM:StateCode` |

### Documentation Keywords (For Rich Metadata)

These keywords are allowed but not parsed as separate fields. They are included in the `Description` field.

| Keyword | Purpose | Used In |
|---------|---------|---------|
| `**Ontology Mappings**:` | Standard ontology codes | NIH CDE templates |
| `**Standard**:` | Compliance standards | NIH CDE templates |
| `**NIH CDE Source**:` | NIH CDE reference URL | NIH CDE templates |
| `**PHI Status**:` | HIPAA PHI classification | Healthcare templates |
| `**Clinical Significance**:` | Medical importance | Healthcare templates |
| `**HL7 Security Classification**:` | HL7 security labels | Healthcare templates |
| `**Access Control Requirements**:` | Access restrictions | Healthcare templates |
| `**De-identification Considerations**:` | De-ID guidance | Healthcare templates |
| `**Calculation Method**:` | Derived field calculation | Calculated fields |
| `**Important Distinctions**:` | Key clarifications | Complex concepts |
| `**Important Notes**:` | Additional context | As needed |

**Note:** You can add these sections for documentation. They will be included in the column's description field for comprehensive metadata capture.

## Cluster-Level Keywords

Used in `## Root Cluster:` and `## Sub-Cluster:` sections.

| Keyword | Description | Example |
|---------|-------------|---------|
| `**Purpose**:` | What this cluster represents | `**Purpose**: Customer identification data` |
| `**Business Context**:` | How cluster is used | `**Business Context**: Required for all transactions` |
| `**Parent**:` | Parent cluster name (sub-clusters only) | `**Parent**: Customer Profile` |

## Dataset-Level Keywords

Used in `# Dataset Overview` section.

| Keyword | Description |
|---------|-------------|
| `**Purpose**:` | Dataset purpose |
| `**Business Context**:` | Dataset usage context |

## Type Reference

### User-Friendly Types

Write types as you know them - the system maps to SDC4 automatically:

| You Write | Description | Maps To |
|-----------|-------------|---------|
| `text` | Free text, strings | `XdString` or `XdToken` (with enumeration) |
| `integer` | Whole numbers | `XdCount` (with units), `XdOrdinal` (with enum), `XdIdentifier` (name pattern) |
| `decimal` | Decimal numbers | `XdQuantity` (with units), `XdFloat`, `XdDouble` |
| `boolean` | True/False, Yes/No | `XdBoolean` |
| `date` | Dates (YYYY-MM-DD) | `XdTemporal` |
| `datetime` | Dates with time | `XdTemporal` |
| `time` | Time only | `XdTemporal` |
| `identifier` | IDs, codes, UUIDs | `XdIdentifier` |
| `email` | Email addresses | `XdString` (validated) |
| `url` | Web links | `XdLink` |

### Explicit SDC4 Types

You can also use explicit SDC4 types:

- `XdString` - Free text
- `XdToken` - Categorical text (with enumeration)
- `XdCount` - Integer counts (with units)
- `XdOrdinal` - Ordinal values (integer with enumeration)
- `XdQuantity` - Measured quantities (decimal with units)
- `XdFloat` - Floating point numbers
- `XdDouble` - High-precision decimals
- `XdBoolean` - Boolean values
- `XdTemporal` - Dates, times, datetimes
- `XdIdentifier` - Identifiers, codes
- `XdLink` - URLs, links
- `XdFile` - File references

## Enumeration Syntax

### List Format (Recommended)

```markdown
**Enumeration**:
  - value1: Description of value 1
  - value2: Description of value 2
  - value3: Description of value 3
```

**Example:**
```markdown
**Enumeration**:
  - active: Account in good standing
  - suspended: Temporarily suspended
  - closed: Permanently closed
```

### Table Format

```markdown
**Enumeration**:
| Value | Label | Description |
|-------|-------|-------------|
| 1 | Active | Account in good standing |
| 2 | Suspended | Temporarily suspended |
| 3 | Closed | Permanently closed |
```

**Important:** Use `**Enumeration**:` not `**Values**:` (deprecated).

## Constraints Syntax

```markdown
**Constraints**:
  - required: true
  - range: [min, max]
  - precision: 2
  - format: "regex or description"
  - unique: true
```

**Examples:**

```markdown
# Age constraint
**Constraints**:
  - required: true
  - range: [0, 120]

# Currency constraint
**Constraints**:
  - required: true
  - precision: 2

# Email constraint
**Constraints**:
  - required: true
  - format: "valid email format"
```

## Semantic Links Syntax

### List Format

```markdown
**Semantic Links**:
- https://terminology.hl7.org/CodeSystem/v3-AdministrativeGender#M
- http://snomed.info/id/248153007
- https://loinc.org/21112-8/
```

Each line is a URI to an ontology term or standard code.

## Component Reuse Syntax

### New Syntax (Recommended)

Reference components by project and label:

```markdown
**ReuseComponent**: @ProjectName:ComponentLabel
```

**Examples:**
```markdown
**ReuseComponent**: @NIEM:StateUSPostalServiceCode
**ReuseComponent**: @HL7v3:AdministrativeGender
**ReuseComponent**: @FHIR:Patient.gender
**ReuseComponent**: @MyLibrary:CustomerEmail
```

### Legacy Syntax (Still Supported)

Reference by CT_ID:

```markdown
**Reuse**: ct_abc123xyz
```

## Intelligent Type Mapping

The system uses context clues to choose the right SDC4 type:

### Name Patterns (Highest Priority)

| Pattern | Maps To | Example |
|---------|---------|---------|
| `*_id`, `*_code`, `*_key` | `XdIdentifier` | `customer_id`, `order_code` |
| `*_url`, `*_link` | `XdLink` | `website_url`, `profile_link` |
| `is_*`, `has_*`, `*_flag` | `XdBoolean` | `is_active`, `has_children` |
| `*_date`, `*_at`, `created`, `updated` | `XdTemporal` | `created_date`, `updated_at` |

### Context-Based Mapping

| Type + Context | Maps To | Reason |
|----------------|---------|--------|
| `integer` + units | `XdCount` | Counted quantity |
| `integer` + enumeration | `XdOrdinal` | Ordinal values |
| `integer` + no context | `XdCount` | Default integer |
| `decimal` + units | `XdQuantity` | Measured quantity |
| `decimal` + precision: 2 | `XdQuantity` | Currency-like |
| `decimal` + precision: >10 | `XdDouble` | High precision |
| `decimal` + no context | `XdFloat` | General decimal |
| `text` + enumeration | `XdToken` | Categorical |
| `text` + no context | `XdString` | Free text |

## Common Patterns

### Identifier Column
```markdown
### Column: customer_id
**Type**: identifier
**Description**: Unique customer identifier
**Constraints**:
  - required: true
  - unique: true
**Examples**: 550e8400-e29b-41d4-a716-446655440000
```

### Measured Quantity
```markdown
### Column: age
**Type**: integer
**Units**: years
**Description**: Customer age in completed years
**Constraints**:
  - required: true
  - range: [0, 120]
**Examples**: 25, 42, 67
```

### Categorical Field
```markdown
### Column: status
**Type**: text
**Description**: Account status
**Enumeration**:
  - active: Account in good standing
  - suspended: Temporarily suspended
  - closed: Permanently closed
**Constraints**:
  - required: true
**Examples**: active, suspended
```

### Currency Field
```markdown
### Column: price
**Type**: decimal
**Units**: USD
**Description**: Product price in US dollars
**Constraints**:
  - required: true
  - precision: 2
  - range: [0, 999999.99]
**Examples**: 19.99, 129.50, 1499.00
```

### Boolean Field
```markdown
### Column: is_active
**Type**: boolean
**Description**: Whether the account is currently active
**Constraints**:
  - required: true
**Examples**: true, false
```

### Date Field
```markdown
### Column: created_date
**Type**: date
**Description**: Date when record was created
**Constraints**:
  - required: true
  - format: "YYYY-MM-DD"
**Examples**: 2025-01-15, 2024-12-31
```

### Reused Component (Standards-Based)
```markdown
### Column: state
**Type**: text
**ReuseComponent**: @NIEM:StateUSPostalServiceCode
**Description**: US state postal code from NIEM standard
**Examples**: CA, NY, TX
```

## Validation Messages

### Helpful Suggestions

The parser provides intelligent feedback:

```
✅ Valid: Column 'age' mapped to XdCount (integer with units: years)

⚠️  Warning: Column 'count' is integer without units.
   Consider adding units (e.g., 'items', 'count') or enumeration if categorical.

❌ Error: Column 'status' has invalid keyword '**Values:**'.
   Did you mean '**Enumeration:**'?
```

### Common Mistakes

| Mistake | Error Message | Fix |
|---------|---------------|-----|
| `**Values**:` | Invalid keyword. Did you mean `**Enumeration:**`? | Use `**Enumeration**:` |
| `**Value**:` | Invalid keyword. Did you mean `**Enumeration:**`? | Use `**Enumeration**:` |
| `**Unit**:` | Invalid keyword. Did you mean `**Units:**`? | Use `**Units**:` |
| `**Example**:` | Invalid keyword. Did you mean `**Examples:**`? | Use `**Examples**:` |
| `**Data Type**:` | Invalid keyword. Did you mean `**Type:**`? | Use `**Type**:` |

## Best Practices

### 1. Use Clear Names
✅ `customer_id`, `birth_date`, `is_active`
❌ `field1`, `data`, `col_a`

### 2. Add Units for Quantities
✅ `**Units**: years`, `**Units**: USD`, `**Units**: kg`
❌ No units for numeric measurements

### 3. Use Enumerations for Categories
✅ List all allowed values with descriptions
❌ Free text for fields with limited options

### 4. Provide Examples
✅ Real-world, representative values
❌ Placeholder values like "xxx" or "test"

### 5. Write Detailed Descriptions
✅ Purpose, usage, business context
❌ Just repeating the column name

### 6. Use Component Reuse for Standards
✅ `@NIEM:StateCode`, `@HL7v3:Gender`
❌ Re-defining standard codes

## Template Checklist

Before uploading your template, verify:

- [ ] YAML front matter has `template_version: "4.0.0"`
- [ ] All columns have `**Type**:` and `**Description**:`
- [ ] Numeric types have `**Units**:` (except counts/IDs)
- [ ] Categorical fields have `**Enumeration**:` (not `**Values**:`)
- [ ] All enumerations use list or table format
- [ ] Examples are provided for each column
- [ ] Constraints are specified where relevant
- [ ] No typos in keyword names
- [ ] Component reuse uses `@Project:Label` syntax

## See Also

- **Template Guide**: `dataset-template.md`
- **Complete Examples**: `examples/` directory
- **Type Mapping Details**: `MD2PD_IMPLEMENTATION.md`
- **NIH CDE Templates**: `docs/NIH-CDE/templates/`
- **Keyword Audit**: `KEYWORD_AUDIT_2025-11-03.md`

## Getting Help

If you see validation errors:
1. Check the error message for suggested fixes
2. Consult this reference guide
3. Review example templates
4. Verify keyword spelling and format

**Last Updated:** 2025-11-03
**Template Version:** 4.0.0
