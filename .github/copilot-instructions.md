# Copilot Instructions for SDMX Technical Documentation

## Project Overview

This repository contains the **SDMX 3.0 Technical Documentation**, specifically the Information Model component. SDMX (Statistical Data and Metadata Exchange) is an international standard for exchanging statistical data and metadata. This is documentation-only—no code implementation, just comprehensive technical specifications.

**Current Status:** Under restructuring for version 3.0.0 (branch: `feature/initial-3.0-creation`).

## Repository Structure

The project is organized into four parallel documentation sections, each with its own MkDocs configuration:

- **`docs/framework/`** → `mkdocs_framework.yml` - High-level SDMX framework introduction
- **`docs/information_model/`** → `mkdocs_information_model.yml` - Complete UML-based Information Model (core content)
- **`docs/logical_interfaces/`** → `mkdocs_logical_interfaces.yml` - Registry specifications and object identification
- **`docs/technical_notes/`** → `mkdocs_technical_notes.yml` - Implementation guidance and best practices

Each section is independently buildable as a separate documentation site.

## Content Conventions

### File Naming Pattern
Files follow a numbered prefix system for ordering:
- `0_Introduction.md` or `0_change_history.md` - Always first
- `1_Actors_and_Use_Cases.md` through `15_Appendix_...` - Sequential chapters
- Numbers determine nav order in MkDocs config

### Document Structure Standards

**UML Diagrams:** Core to this documentation. All diagrams are in `docs/*/media/` as SVG (preferred) or PNG:
```markdown
![](media/image36.png){ width="550" }
/// figure-caption | 10
SDMX Identification, Maintenance and Versioning
///
```
- Use `/// figure-caption` blocks (custom MkDocs extension syntax)
- Optional `| N` syntax indicates figure number
- SVG preferred for UML class diagrams; PNG for complex process diagrams

**Class Definitions:** Use standardized table format:
```markdown
| Class | Feature | Description |
| :--- | :--- | :--- |
| `ClassName` |  |  |
|  | `attributeName` |  |
|  | `associationName` |  |
|  | `+roleName` |  |
```
- Abstract classes shown in *italic Courier*: `*AnnotableArtefact*`
- Attributes/associations in backticks
- Roles prefixed with `+`

**Cross-References:** Use relative paths:
```markdown
[SDMX SECTION 05](../../logical_interfaces/logical_interfaces/6_Identification_of_SDMX_Objects.md)
[Section 2](../../information_model/information_model/0_Introduction.md)
```

### Terminology Consistency

- **Data Structure Definition (DSD)** - Primary term; "Key Family" is legacy synonym
- **Maintainable Artefact** - British spelling throughout ("artefact" not "artifact")
- **Information Model (SDMX-IM)** - Refers to the UML conceptual design
- **Metadata** types:
  - *Structural metadata* - Defines structure (DSDs, codelists, concepts)
  - *Reference metadata* - Quality, methodology, annotations
  - *Provisioning metadata* - Registration, submission info

## Content Architecture Patterns

### Information Model Documents (`docs/information_model/`)
Each chapter follows this pattern:
1. **Introduction** - Context and purpose
2. **Inheritance View** - UML class hierarchy diagram
3. **Relationship View** - Association diagrams
4. **Definitions** - Tabular class/attribute/role definitions

Key packages (each gets a dedicated chapter):
- `2_SDMX_Base_Package.md` - Foundation: Annotable→Identifiable→Nameable→Versionable→Maintainable
- `3_Specific_Item_Schemes.md` - Codelists, Concepts, Categories
- `4_Data_Structure_Definition_and_Dataset.md` - Core data modeling
- `7_Hierarchy.md`, `8_Structure_Map.md` - Advanced mapping features

### Technical Notes (`docs/technical_notes/`)
Implementation-focused guidance on:
- `3_General_Notes_for_Implementers.md` - Versioning, representations
- `5_Codelist.md` - Extension mechanisms, discriminated unions
- `11_Validation_and_Transformation_Language__VTL_.md` - VTL 2.0 integration
- `13_ANNEX_Semantic_Versioning.md` - SDMX versioning rules

## Version Context

**SDMX 3.0 Changes from 2.1:**
- **Deprecated:** EDI format, SOAP APIs, some XML data messages
- **Breaking changes:** Structure mapping, reference metadata redesigned
- **New:** Semantic versioning for metadata artefacts, enhanced VTL support
- **Modernization:** RESTful API improvements, richer data query syntax

## Editing Guidelines

### When Adding New Documentation

1. **Choose the right section:**
   - Framework → Introductory/overview content
   - Information Model → UML class definitions
   - Technical Notes → Implementation guidance
   - Logical Interfaces → Registry/service specifications

2. **Follow numbering:** Insert files maintaining sequential order; update MkDocs YAML nav

3. **Include diagrams:** Place in corresponding `media/` folder; prefer SVG for scalability

4. **Use inheritance properly:** Check `2_SDMX_Base_Package.md` for what classes already provide (don't redocument inherited features)

### When Editing Existing Content

- **Preserve UML precision:** Class names, attribute names, cardinalities are normative
- **Check cross-references:** Verify relative paths still resolve after changes
- **Maintain figure numbering:** Keep `/// figure-caption | N` sequences consistent
- **Test locally:** Changes affect multiple interlinked MkDocs sites

### Common Patterns to Maintain

**Namespace disambiguation:**
```markdown
The `DataStructureDefinition` is the class name...
```
Always use backticks for class/attribute names in prose.

**External links:**
```markdown
The SDMX Technical Working Group (TWG): [GitHub repository](https://github.com/sdmx-twg)
```

**Appendix references:**
```markdown
See the Appendix [A Short Guide to UML in the SDMX Information Model](./15_Appendix_1:_A_Short_Guide_to_UML_in_the_SDMX_Information_Model.md)
```

## Key Files for Context

- `README.md` - Repository overview and documentation structure
- `docs/information_model/0_Introduction.md` - Document relationships and UML notation guide
- `docs/framework/0_framework-introduction.md` - Complete SDMX technical standards overview
- `docs/information_model/2_SDMX_Base_Package.md` - Foundation for all classes
- `docs/information_model/0_change_history.md` - Evolution from 1.0→2.0→2.1→3.0

## Building Documentation

The SDMX documentation is built **jointly from multiple repositories** as a unified documentation site. This repository is combined with the REST API, SDMX-ML, SDMX-JSON, and SDMX-CSV repositories in a centralized build process coordinated by the SDMX documentation repository.

**Important:** The MkDocs configuration files (`mkdocs_framework.yml`, `mkdocs_information_model.yml`, `mkdocs_logical_interfaces.yml`, `mkdocs_technical_notes.yml`) define the **navigation structure** for their respective sections within the unified documentation. They are not intended for standalone local builds.
