# SDMX 3.1 Technical Documentation - Information Model Component

[![Under Restructuring](https://img.shields.io/badge/status-Under%20Restructuring-red?style=flat-square)](https://github.com/HMS-Analytical-Software/sdmx-technical-documentation-im)
[![SDMX 3.0](https://img.shields.io/badge/SDMX-3.0-blue?style=flat-square)](https://sdmx.org)
[![Documentation](https://img.shields.io/badge/docs-MkDocs-green?style=flat-square)](https://www.mkdocs.org/)

!!! note Only the information model section contains the content for SDMX
version 3.1. All other material still refers to SDMX 3.0.

This repository contains the **SDMX 3.1 Technical Specifications** documentation
for the **Information Model** component and related sections. The Statistical
Data and Metadata Exchange (SDMX) initiative provides international standards
for exchanging statistical data and metadata.

> **Note:** This repository is currently under active restructuring for SDMX
> version 3.1.0.

## 📚 Documentation Sections

This repository comprises four interconnected documentation sections covering
different aspects of the SDMX standard:

### Section 1: Framework for SDMX Technical Standards

**Location:** `docs/framework/` | **Config:** `mkdocs_framework.yml`

High-level introduction to the SDMX technical standards, including:

- Overview of SDMX processes and business scope
- Introduction to the Information Model
- SDMX transmission formats (SDMX-ML, SDMX-JSON, SDMX-CSV)
- Validation and Transformation Language (VTL)

### Section 2: SDMX Information Model (Core Content)

**Location:** `docs/information_model/` | **Config:**
`mkdocs_information_model.yml`

Complete UML-based specification of the SDMX Information Model:

- **Base Package**: Foundation classes
  (Annotable→Identifiable→Nameable→Versionable→Maintainable)
- **Item Schemes**: Codelists, Concepts, Categories, Organizations
- **Data Structures**: Data Structure Definitions (DSD) and Datasets
- **Metadata Structures**: Metadata Structure Definitions (MSD) and Metadata
  Sets
- **Advanced Features**: Hierarchies, Structure Mapping, Constraints, Cubes
- **VTL Support**: Validation and Transformation Language integration
- **UML Appendix**: Guide to UML notation used throughout

### Section 5: SDMX Registry Specification - Logical Interfaces

**Location:** `docs/logical_interfaces/` | **Config:**
`mkdocs_logical_interfaces.yml`

Registry specifications including:

- Identification of SDMX objects
- Implementation notes for registry operations

### Section 6: SDMX Technical Notes

**Location:** `docs/technical_notes/` | **Config:** `mkdocs_technical_notes.yml`

Detailed implementation guidance for developers:

- General notes for implementers (versioning, representations)
- Reference metadata patterns
- Codelist extension mechanisms and discriminated unions
- Geospatial information support
- Constraints and validation
- Structure mapping techniques
- VTL implementation guidance
- Semantic versioning rules (ANNEX)

## 🎯 SDMX Version

**Current Version:** SDMX 3.1.0 (under development)

## 🛠️ Building Documentation

The SDMX documentation is built **jointly from multiple repositories** as a
unified documentation site. This repository is combined with:

- **sdmx-twg/sdmx-rest** - REST API specifications
- **sdmx-twg/sdmx-ml** - SDMX-ML (XML format) specifications
- **sdmx-twg/sdmx-json** - SDMX-JSON specifications
- **sdmx-twg/sdmx-csv** - SDMX-CSV specifications

The overall build process is coordinated in the **SDMX documentation
repository** (link will be inserted once available).

**Note:** The MkDocs configuration files in this repository
(`mkdocs_framework.yml`, `mkdocs_information_model.yml`,
`mkdocs_logical_interfaces.yml`, `mkdocs_technical_notes.yml`) are used to
**define the navigation structure** for their respective sections within the
unified documentation. They are not intended for standalone local builds of
individual sections.

## ✍️ Markdown Formatting Conventions

This documentation uses standard Markdown with specific conventions and
extensions:

### File Naming

Files use **numbered prefixes** to control navigation order:

- `0_Introduction.md` or `0_change_history.md` - Always first
- `1_Actors_and_Use_Cases.md` through `15_Appendix_...` - Sequential chapters
- Numbers determine the order in MkDocs navigation

### UML Diagrams

Diagrams are stored in `docs/*/media/` folders as SVG (preferred) or PNG:

```markdown
![](media/image36.png){ width="550" } /// figure-caption | 10 SDMX
Identification, Maintenance and Versioning ///
```

- `/// figure-caption` blocks use a custom MkDocs extension
- Optional `| N` indicates the figure number
- **SVG preferred** for UML class diagrams (scalable)
- **PNG acceptable** for complex process diagrams

### Class Definitions

Standardized table format for UML classes:

```markdown
| Class       | Feature           | Description |
| :---------- | :---------------- | :---------- |
| `ClassName` |                   |             |
|             | `attributeName`   |             |
|             | `associationName` |             |
|             | `+roleName`       |             |
```

- Abstract classes: `*AnnotableArtefact*` (italic monospace)
- Attributes/associations: `` `attributeName` `` (backticks)
- Roles: `` `+roleName` `` (prefix with +)

### Cross-References

Use **relative paths** for internal links:

```markdown
[SDMX SECTION 05](../../logical_interfaces/logical_interfaces/6_Identification_of_SDMX_Objects.md)
[Section 2](../../information_model/information_model/0_Introduction.md)
```

### Terminology Standards

- **Data Structure Definition (DSD)** - Standard term; "Key Family" is legacy
  synonym
- **Maintainable Artefact** - British spelling ("artefact" not "artifact")
- **Information Model (SDMX-IM)** - Refers to UML conceptual design
- Always use backticks for class/attribute names in prose:
  ``The `DataStructureDefinition` class...``

## 🔍 Markdown Linting

**A Markdown linter is strongly recommended** to maintain consistency and catch
formatting issues.

### Recommended Tools

- **[markdownlint-cli](https://github.com/igorshubovych/markdownlint-cli)** -
  Command-line tool
- **[VS Code markdownlint extension](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)** -
  Editor integration

### Installation

```bash
# Using npm
npm install -g markdownlint-cli

# Using VS Code
code --install-extension DavidAnson.vscode-markdownlint
```

### Suggested Configuration

Key rules to enforce:

- **MD001**: Heading levels increment by one
- **MD013**: Line length limits (disabled for tables)
- **MD033**: Allow inline HTML (for `{ width="550" }` syntax)
- **MD040**: Fenced code blocks should have language specified
- **MD051**: Link fragments should be valid

Note: Some custom MkDocs syntax (like `/// figure-caption`) may trigger linter
warnings - these can be safely ignored or configured as exceptions.

## 🤝 Contributing

### Before Contributing

1. Review existing content structure in the appropriate `docs/*/` folder
2. Check `.github/copilot-instructions.md` for detailed conventions
3. Ensure UML precision - class names, attributes, and cardinalities are
   normative
4. Maintain consistent cross-referencing with relative paths

### Editing Checklist

- [ ] Preserve UML precision and normative terminology
- [ ] Verify cross-references resolve correctly
- [ ] Maintain figure numbering sequences
- [ ] Test with `mkdocs build` for affected sections
- [ ] Run markdown linter
- [ ] Check that all diagrams are properly referenced

## 📖 Key Reference Files

Essential files for understanding the documentation structure:

- **Repository overview**: `README.md` (this file)
- **AI agent guidance**: `.github/copilot-instructions.md`
- **Document relationships**: `docs/information_model/0_Introduction.md`
- **SDMX overview**: `docs/framework/0_framework-introduction.md`
- **Foundation classes**: `docs/information_model/2_SDMX_Base_Package.md`
- **Version history**: `docs/information_model/0_change_history.md`
- **UML notation guide**:
  `docs/information_model/15_Appendix_1:_A_Short_Guide_to_UML_in_the_SDMX_Information_Model.md`

## 🔗 Related Resources

- **SDMX Official Website**: <https://www.sdmx.org>
- **SDMX Technical Working Group**: <https://github.com/sdmx-twg>
- **REST API Specification**: <https://github.com/sdmx-twg/sdmx-rest>
- **SDMX-ML (XML format)**: <https://github.com/sdmx-twg/sdmx-ml>
- **SDMX-JSON**: <https://github.com/sdmx-twg/sdmx-json>
- **SDMX-CSV**: <https://github.com/sdmx-twg/sdmx-csv>

## 📜 License

[License information to be added - typically the SDMX specifications are openly
available]

## 📧 Contact

For questions about SDMX specifications, please refer to the
[SDMX website](https://sdmx.org) or contact the SDMX Technical Working Group.
