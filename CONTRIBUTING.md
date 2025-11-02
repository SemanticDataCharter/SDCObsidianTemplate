# Contributing to SDCStudio Obsidian Template

Thank you for your interest in contributing to the SDCStudio Obsidian Template! This project is part of [Axius SDC, Inc.'s](https://axius-sdc.github.io) commitment to open source and the [Semantic Data Charter](https://github.com/SemanticDataCharter) ecosystem.

We welcome contributions of all kinds: bug reports, feature suggestions, documentation improvements, and code contributions.

---

## 🌟 How to Contribute

### Reporting Bugs

If you find a bug, please [open an issue](https://github.com/AxiusSDC/SDCObsidianTemplate/issues/new) with:

1. **Clear title** - Describe the issue concisely
2. **Description** - What happened vs what you expected
3. **Steps to reproduce** - Numbered list to recreate the issue
4. **Environment**:
   - Obsidian version
   - Templater version
   - Operating system
   - Template version
5. **Screenshots** - If applicable
6. **Error messages** - Copy any error messages from Obsidian console

**Template**:
```markdown
### Bug Description
[Clear description of the bug]

### Steps to Reproduce
1. Open Obsidian
2. Insert template
3. [Specific action that triggers bug]

### Expected Behavior
[What should happen]

### Actual Behavior
[What actually happens]

### Environment
- Obsidian: v1.x.x
- Templater: v1.x.x
- OS: [Windows/Mac/Linux]
- Template: v4.0.0

### Screenshots
[If applicable]

### Error Messages
```
[Paste error messages here]
```
```

---

### Suggesting Features

We love new ideas! [Open a feature request](https://github.com/AxiusSDC/SDCObsidianTemplate/issues/new) with:

1. **Problem statement** - What problem does this solve?
2. **Proposed solution** - How would this feature work?
3. **Alternatives considered** - What other approaches did you think about?
4. **Use case** - Real-world scenario where this helps
5. **SDC4 compliance** - How does this align with SDC4?

**Template**:
```markdown
### Feature Request

**Problem**: [What problem needs solving?]

**Proposed Solution**: [How should this work?]

**Use Case**: [Real-world example]

**Alternatives**: [Other approaches considered]

**SDC4 Compliance**: [How does this fit with SDC4?]
```

---

### Improving Documentation

Documentation is critical! Ways to help:

- **Fix typos or unclear explanations** - Submit PR directly
- **Add examples** - Real-world use cases help everyone
- **Translate** - Help make docs accessible in other languages
- **Create tutorials** - Blog posts, videos, guides
- **Update screenshots** - Keep visuals current

**Process**:
1. Fork the repository
2. Edit files in `docs/` folder
3. Submit pull request
4. Describe what you improved and why

---

### Contributing Code

#### Getting Started

1. **Fork the repository**
   ```bash
   # Via GitHub web interface or:
   gh repo fork AxiusSDC/SDCObsidianTemplate --clone
   ```

2. **Create a branch**
   ```bash
   cd SDCObsidianTemplate
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/bug-description
   ```

3. **Make your changes**
   - Edit `templates/ObsidianDataSetTemplate.md` for template changes
   - Edit `snippets/sdcstudio-theme.css` for styling changes
   - Update `docs/` for documentation changes

4. **Test thoroughly**
   - Test in Obsidian with Templater plugin
   - Try different scenarios and edge cases
   - Verify CSS doesn't break in light/dark themes
   - Ensure markdown output is SDC4-compliant

5. **Commit your changes**
   ```bash
   git add .
   git commit -m "feat: Add new feature description"
   # or
   git commit -m "fix: Fix bug description"
   ```

6. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

7. **Open a pull request**
   - Go to GitHub and click "New Pull Request"
   - Fill out the PR template
   - Link related issues

---

### Commit Message Guidelines

We follow [Conventional Commits](https://www.conventionalcommits.org/):

**Format**: `type(scope): description`

**Types**:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: CSS or formatting changes (no logic change)
- `refactor`: Code refactoring (no behavior change)
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples**:
```bash
feat(template): Add support for multi-select enumerations
fix(css): Fix table header styling in dark mode
docs(install): Add troubleshooting section for Windows
style(css): Improve contrast ratio for accessibility
refactor(template): Simplify type mapping logic
```

---

### Pull Request Guidelines

**Before submitting**:
- [ ] Code follows existing style and patterns
- [ ] Template runs without errors in Obsidian
- [ ] CSS doesn't break existing styling
- [ ] Documentation is updated (if needed)
- [ ] CHANGELOG.md is updated
- [ ] Testing completed in multiple scenarios
- [ ] Commit messages follow convention

**PR template**:
```markdown
## Description
[Clear description of what this PR does]

## Motivation
[Why is this change needed?]

## Changes Made
- [List of specific changes]
- [Another change]

## Testing
- [ ] Tested in Obsidian v1.x.x
- [ ] Tested with Templater v1.x.x
- [ ] Tested on [Windows/Mac/Linux]
- [ ] Verified SDC4 compliance
- [ ] CSS tested in light/dark themes

## Screenshots
[If applicable]

## Related Issues
Fixes #[issue number]
Related to #[issue number]

## Checklist
- [ ] Documentation updated
- [ ] CHANGELOG.md updated
- [ ] Follows commit message guidelines
- [ ] No breaking changes (or clearly documented)
```

---

## 🎨 Code Style Guidelines

### Template Code (JavaScript)

**File**: `templates/ObsidianDataSetTemplate.md`

**Style**:
- Use `const` for constants, `let` for variables
- Meaningful variable names: `datasetName`, not `dn`
- Comment complex logic
- Use async/await for Templater prompts
- Update `content` incrementally with `editor.setValue()`
- Add progress indicators for long operations

**Example**:
```javascript
// Good
const datasetName = await tp.system.prompt("Dataset Name:", tp.file.title);
const description = await tp.system.prompt("Description:", "Brief description");

// Bad
let name = await tp.system.prompt("Name:");
let desc = await tp.system.prompt("Desc:");
```

### CSS Code

**File**: `snippets/sdcstudio-theme.css`

**Style**:
- Use CSS custom properties (variables) for colors
- Group related selectors together
- Comment each major section
- Use specific selectors (`.markdown-preview-view` prefix)
- Include both preview and edit mode selectors
- Maintain WCAG AA color contrast

**Example**:
```css
/* Good */
:root {
    --sdc-primary: #0a2342;
    --sdc-secondary: #2ca58d;
}

.markdown-preview-view h1,
.markdown-preview-view h2 {
    color: var(--sdc-primary);
}

/* Bad */
h1, h2 {
    color: #0a2342;
}
```

### Documentation (Markdown)

**Files**: `docs/*.md`, `README.md`, `CHANGELOG.md`

**Style**:
- Use headers hierarchically (h1 → h2 → h3)
- Include code examples in fenced blocks with language
- Use tables for structured data
- Add emoji sparingly for visual hierarchy
- Link to related resources
- Keep line length reasonable (~100 chars)

---

## 🧪 Testing Guidelines

### Template Testing

**Test scenarios**:
1. **Basic flow** - Create simple dataset with 2 columns
2. **Edge cases** - Empty prompts, cancel operations
3. **Scalability** - Create dataset with 10+ columns
4. **Component reuse** - Test @ProjectName:ComponentLabel syntax
5. **All types** - Test each data type (text, integer, decimal, boolean, etc.)
6. **Constraints** - Test range, precision, format, enumeration
7. **Sub-clusters** - Create nested cluster structures
8. **YAML validation** - Ensure front matter is valid YAML

### CSS Testing

**Test scenarios**:
1. **Light theme** - Verify all colors are correct
2. **Dark theme** - Ensure readability and contrast
3. **Tables** - Check header colors, row striping, hover states
4. **Links** - Verify teal color and hover effect
5. **Headings** - Check blue color and sizing
6. **Code blocks** - Test inline and fenced code styling
7. **Lists** - Verify bullet/number colors
8. **Blockquotes** - Check teal border and background

### Integration Testing

1. **Upload to SDCStudio** - Verify markdown parses correctly
2. **MD2PD parser** - Ensure no CSS in file content
3. **XSD generation** - Check SDCStudio generates valid XSD
4. **Type mapping** - Verify user types map to correct SDC4 XD types

---

## 📜 License

By contributing, you agree that your contributions will be licensed under the Apache License 2.0, the same license as this project.

See [LICENSE](LICENSE) for full details.

---

## 🏢 Code of Conduct

### Our Pledge

We are committed to providing a welcoming and inclusive environment for all contributors, regardless of:
- Age, body size, disability, ethnicity, sex characteristics
- Gender identity and expression, level of experience
- Education, socio-economic status, nationality
- Personal appearance, race, religion, sexual identity and orientation

### Our Standards

**Positive behaviors**:
- Using welcoming and inclusive language
- Being respectful of differing viewpoints
- Gracefully accepting constructive criticism
- Focusing on what is best for the community
- Showing empathy towards other community members

**Unacceptable behaviors**:
- Trolling, insulting/derogatory comments, personal attacks
- Public or private harassment
- Publishing others' private information without permission
- Other conduct which could reasonably be considered inappropriate

### Enforcement

Instances of abusive, harassing, or otherwise unacceptable behavior may be reported to the project maintainers. All complaints will be reviewed and investigated promptly and fairly.

---

## 🤝 Recognition

Contributors will be recognized in:
- GitHub contributor graph
- Release notes (for significant contributions)
- Special mentions in README (for major features)

---

## 📞 Questions?

- **General questions**: [Open a discussion](https://github.com/AxiusSDC/SDCObsidianTemplate/discussions)
- **Bug reports**: [Open an issue](https://github.com/AxiusSDC/SDCObsidianTemplate/issues)
- **Security issues**: Email [security@axiussdc.com](mailto:security@axiussdc.com) (if applicable)

---

## 🚀 Getting Help

If you're new to contributing to open source:
- [First Timers Only](https://www.firsttimersonly.com/)
- [How to Contribute to Open Source](https://opensource.guide/how-to-contribute/)
- [GitHub Skills](https://skills.github.com/)

Look for issues labeled `good first issue` to get started!

---

**Thank you for contributing to the SDCStudio Obsidian Template!** 🎉

Your contributions help make semantic data modeling accessible to everyone.

---

**Made with ❤️ by the Axius SDC community**
