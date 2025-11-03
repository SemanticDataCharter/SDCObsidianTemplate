<%*
/*
 * SDCStudio Dataset Template v4.0.0
 * ===================================
 *
 * This template creates SDC4-compliant dataset descriptions for upload to SDCStudio.
 *
 * FEATURES:
 * - User-friendly type system (text, integer, decimal, boolean, date, etc.)
 * - Optional component reuse from NIEM, FHIR, HL7v3, openEHR, and other projects
 * - Structured constraints (required, unique, range, precision, format)
 * - LLM enrichment toggle for semantic enhancement
 * - Progress indicators - no more hanging!
 * - Easy expansion via copy-paste templates
 *
 * USAGE:
 * 1. Template will prompt for dataset basics (name, description, domain, etc.)
 * 2. Create root cluster with 2-3 columns interactively
 * 3. Optionally add sub-clusters
 * 4. For more columns, use the copy-paste templates at the bottom
 *
 * WHAT'S NEW IN v4.0.0:
 * - Non-blocking prompts with visual feedback (no hanging!)
 * - Component reuse support (@ProjectName:ComponentLabel)
 * - User-friendly types that map to SDC4 automatically
 * - Structured constraints in proper YAML format
 * - Complete YAML front matter
 * - Professional markdown output
 *
 */

// Helper function to build content incrementally
let content = "";
const editor = app.workspace.activeLeaf.view.editor;

function updateContent(newContent) {
    content += newContent;
    editor.setValue(content);
}

function showProgress(message) {
    updateContent(`\n<!-- ⚙️  ${message}... -->\n`);
}

// =============================================================================
// PHASE 1: Dataset Metadata Collection
// =============================================================================

showProgress("Setting up dataset metadata");

const datasetName = await tp.system.prompt("Dataset Name:", tp.file.title);
const datasetDescription = await tp.system.prompt("Dataset Description:", "Brief description of the dataset");
const domain = await tp.system.prompt("Domain (optional):", "Healthcare, Finance, Retail, Government, etc.", false) || "";
const creator = await tp.system.prompt("Creator/Team (optional):", "Your name or team name", false) || "";
const projectLink = await tp.system.prompt("Link to existing project (optional):", "project_ct_id or leave blank", false) || "";
const enableLLM = await tp.system.suggester(
    ["Yes - Enable AI semantic enrichment", "No - Fast parsing only"],
    [true, false],
    false,
    "Enable LLM enrichment for semantic enhancement?"
);

const purpose = await tp.system.prompt("Dataset Purpose:", "Why this dataset exists and what it's used for");
const businessContext = await tp.system.prompt("Business Context:", "How this data is used, who uses it, key use cases");
const source = await tp.system.prompt("Data Source (optional):", "Database, API, manual collection, etc.", false) || "";
const frequency = await tp.system.prompt("Update Frequency (optional):", "Daily, weekly, monthly, real-time, etc.", false) || "";
const scope = await tp.system.prompt("Scope (optional):", "Time period, geographic area, subject matter, etc.", false) || "";

// Build YAML front matter
content = `---
template_version: "4.0.0"
creation_date: <% tp.file.creation_date() %>
last_modified: <% tp.file.last_modified_date("YYYY-MM-DD HH:mm:ss") %>
dataset:
  name: "${datasetName}"
  description: "${datasetDescription}"`;

if (domain) content += `\n  domain: "${domain}"`;
if (creator) content += `\n  creator: "${creator}"`;
if (projectLink) content += `\n  project: "${projectLink}"`;

content += `\nenrichment:
  enable_llm: ${enableLLM}
---

# Dataset Overview

${datasetDescription}

**Purpose**: ${purpose}

**Business Context**: ${businessContext}`;

if (source) content += `\n**Source**: ${source}`;
if (frequency) content += `\n**Frequency**: ${frequency}`;
if (scope) content += `\n**Scope**: ${scope}`;

editor.setValue(content);

// =============================================================================
// PHASE 2: Root Cluster Setup
// =============================================================================

showProgress("Setting up root cluster");

const rootClusterName = await tp.system.prompt("Root Cluster Name:", "Main Data");
const rootClusterDesc = await tp.system.prompt("Root Cluster Description:", "Main data cluster containing all data elements");
const rootClusterPurpose = await tp.system.prompt("Root Cluster Purpose (optional):", "What this cluster represents", false) || "";

content += `\n\n## Root Cluster: ${rootClusterName}

${rootClusterDesc}`;

if (rootClusterPurpose) content += `\n\n**Purpose**: ${rootClusterPurpose}`;

editor.setValue(content);

// =============================================================================
// PHASE 3: Column Creation (2-3 columns with all features)
// =============================================================================

// Type mapping information
const typeMapping = {
    "text": "Text/strings → XdString or XdToken (with enum)",
    "integer": "Whole numbers → XdCount (with units) / XdOrdinal (with enum) / XdIdentifier (if _id pattern)",
    "decimal": "Decimal numbers → XdQuantity (with units) / XdFloat / XdDouble",
    "boolean": "True/False → XdBoolean",
    "date": "Dates (YYYY-MM-DD) → XdTemporal",
    "datetime": "Dates with time → XdTemporal",
    "identifier": "IDs, codes, UUIDs → XdIdentifier",
    "email": "Email addresses → XdString (validated)",
    "url": "Web links → XdLink"
};

async function createColumn() {
    const columnName = await tp.system.prompt("Column Name:");

    // Check for component reuse
    const wantsReuse = await tp.system.suggester(
        ["No - Create new component", "Yes - Reuse existing component (@ProjectName:Label)"],
        [false, true],
        false,
        "Reuse an existing component from another project?"
    );

    let reuseRef = "";
    if (wantsReuse) {
        reuseRef = await tp.system.prompt("Component Reference:", "@ProjectName:ComponentLabel (e.g., @NIEM:StateUSPostalServiceCode)");
    }

    // Type selection with mapping hints
    const typeOptions = Object.keys(typeMapping);
    const typeDescriptions = typeOptions.map(t => `${t} - ${typeMapping[t]}`);
    const selectedType = await tp.system.suggester(typeDescriptions, typeOptions, false, "Select data type:");

    const description = await tp.system.prompt("Description:", "Detailed description of this data element");

    // Conditional prompts based on type
    let units = "";
    if (selectedType === "integer" || selectedType === "decimal") {
        units = await tp.system.prompt("Units (optional):", "years, USD, items, meters, etc.", false) || "";
    }

    // Constraints
    const required = await tp.system.suggester(["Optional (0..1)", "Required (1..1)"], [false, true], false, "Is this field required?");
    const unique = await tp.system.suggester(["No", "Yes - Must be unique"], [false, true], false, "Must values be unique?");

    let minRange = "";
    let maxRange = "";
    let precision = "";
    let format = "";

    if (selectedType === "integer" || selectedType === "decimal") {
        const hasRange = await tp.system.suggester(["No range constraints", "Yes - Specify min/max"], [false, true], false, "Add range constraints?");
        if (hasRange) {
            minRange = await tp.system.prompt("Minimum value (optional):", "", false) || "";
            maxRange = await tp.system.prompt("Maximum value (optional):", "", false) || "";
        }
    }

    if (selectedType === "decimal") {
        precision = await tp.system.prompt("Decimal precision (optional):", "Number of decimal places (e.g., 2 for money)", false) || "";
    }

    if (selectedType === "text" || selectedType === "email") {
        format = await tp.system.prompt("Format/Pattern (optional):", "Regex or description of valid format", false) || "";
    }

    const businessRules = await tp.system.prompt("Business Rules (optional):", "Validation rules, constraints, special logic", false) || "";
    const examples = await tp.system.prompt("Example Values:", "Comma-separated examples (e.g., value1, value2, value3)");

    // Enumeration
    const hasEnum = await tp.system.suggester(["No", "Yes - Add enumeration values"], [false, true], false, "Does this column have a fixed set of values?");
    let enumValues = [];
    if (hasEnum) {
        const enumFormat = await tp.system.suggester(
            ["Simple list (value: description)", "Table format (Value | Label | Description)"],
            ["simple", "table"],
            false,
            "Choose enumeration format:"
        );

        let addingValues = true;
        while (addingValues) {
            const enumValue = await tp.system.prompt(`Enumeration Value ${enumValues.length + 1}:`, "Value or code");
            const enumDesc = await tp.system.prompt("Description:", "What this value means");
            enumValues.push({ value: enumValue, description: enumDesc });

            const addAnother = await tp.system.suggester(["Add another value", "Done"], [true, false], false, "Add another enumeration value?");
            addingValues = addAnother;
        }
    }

    // Build column markdown
    let columnMd = `\n\n### Column: ${columnName}\n`;
    columnMd += `**Type**: ${selectedType}\n`;
    columnMd += `**Description**: ${description}\n`;

    if (reuseRef) {
        columnMd += `**ReuseComponent**: ${reuseRef}\n`;
    }

    if (units) {
        columnMd += `**Units**: ${units}\n`;
    }

    // Constraints
    let hasConstraints = required || unique || minRange || maxRange || precision || format;
    if (hasConstraints) {
        columnMd += `**Constraints**:\n`;
        columnMd += `  - required: ${required}\n`;
        if (unique) columnMd += `  - unique: true\n`;
        if (minRange || maxRange) columnMd += `  - range: [${minRange || ""}${minRange || maxRange ? ", " : ""}${maxRange || ""}]\n`;
        if (precision) columnMd += `  - precision: ${precision}\n`;
        if (format) columnMd += `  - format: "${format}"\n`;
    }

    if (businessRules) {
        columnMd += `**Business Rules**: ${businessRules}\n`;
    }

    columnMd += `**Examples**: ${examples}\n`;

    // Enumeration
    if (enumValues.length > 0) {
        columnMd += `\n**Enumeration**:\n`;
        for (const ev of enumValues) {
            columnMd += `  - ${ev.value}: ${ev.description}\n`;
        }
    }

    return columnMd;
}

// Create 2-3 columns
showProgress("Creating columns");

const column1 = await createColumn();
content += column1;
editor.setValue(content);

const addColumn2 = await tp.system.suggester(["Yes - Add another column", "No - Continue"], [true, false], false, "Add a second column?");
if (addColumn2) {
    const column2 = await createColumn();
    content += column2;
    editor.setValue(content);

    const addColumn3 = await tp.system.suggester(["Yes - Add third column", "No - Continue"], [true, false], false, "Add a third column?");
    if (addColumn3) {
        const column3 = await createColumn();
        content += column3;
        editor.setValue(content);
    }
}

// =============================================================================
// PHASE 4: Sub-Cluster (Optional)
// =============================================================================

const addSubCluster = await tp.system.suggester(["No - Continue", "Yes - Add sub-cluster"], [false, true], false, "Add a sub-cluster?");

if (addSubCluster) {
    showProgress("Creating sub-cluster");

    const subClusterName = await tp.system.prompt("Sub-Cluster Name:");
    const subClusterDesc = await tp.system.prompt("Sub-Cluster Description:");
    const subClusterPurpose = await tp.system.prompt("Sub-Cluster Purpose (optional):", "", false) || "";

    content += `\n\n## Sub-Cluster: ${subClusterName}

${subClusterDesc}

**Purpose**: ${subClusterPurpose}
**Parent**: ${rootClusterName}`;

    editor.setValue(content);

    const addSubColumn = await tp.system.suggester(["Yes - Add column to sub-cluster", "No - Skip"], [true, false], false, "Add a column to this sub-cluster?");
    if (addSubColumn) {
        const subColumn = await createColumn();
        content += subColumn;
        editor.setValue(content);
    }
}

// =============================================================================
// PHASE 5: Helper Templates
// =============================================================================

content += `

<!--
===============================================================================
COPY-PASTE TEMPLATES & KEYWORD REFERENCE
===============================================================================

📚 COMPREHENSIVE KEYWORD REFERENCE:
   See docs/KEYWORD_REFERENCE.md for complete documentation of all keywords,
   syntax, examples, and best practices.

Need to add more columns? Copy the template below and fill in the details:

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
  - value3: Description 3

---

Need a sub-cluster? Copy this template:

## Sub-Cluster: [cluster_name]

[Description]

**Purpose**: [What this cluster represents]
**Parent**: [Parent cluster name]

### Column: [column_name]
[Use column template above]

---

ENUMERATION TABLE FORMAT (Alternative to simple list):

**Enumeration**:
| Value | Label | Description |
|-------|-------|-------------|
| 1 | Active | Account in good standing |
| 2 | Suspended | Temporarily suspended |
| 3 | Closed | Permanently closed |

---

USER-FRIENDLY TYPE REFERENCE:

| Type You Write | Maps To SDC4 | When to Use |
|----------------|--------------|-------------|
| text | XdString or XdToken | Free text, strings, categorical with enum |
| integer | XdCount, XdOrdinal, XdIdentifier | Whole numbers (add units for XdCount) |
| decimal | XdQuantity, XdFloat, XdDouble | Numbers with decimals (add units for XdQuantity) |
| boolean | XdBoolean | True/False, Yes/No |
| date | XdTemporal | Dates only (YYYY-MM-DD) |
| datetime | XdTemporal | Dates with time |
| identifier | XdIdentifier | IDs, codes, UUIDs, reference numbers |
| email | XdString | Email addresses (validated) |
| url | XdLink | Web links, URLs, URIs |

INTELLIGENT TYPE MAPPING:
- Column name contains "_id" → automatically suggests identifier
- Column name starts with "is_" or "has_" → automatically suggests boolean
- Column name ends with "_date" or "_at" → automatically suggests datetime
- integer/decimal with units → automatically becomes XdCount/XdQuantity
- text/integer with enumeration → automatically becomes XdToken/XdOrdinal

-->%>
