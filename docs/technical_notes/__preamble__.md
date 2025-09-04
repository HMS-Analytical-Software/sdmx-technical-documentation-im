| <p>SDMX STANDARDS: SECTION 6</p><br><p>TECHNICAL NOTES</p><br><p>Version 3.0</p> |
| :--- |
| October 2021 |


Table 1: SDMX-ML Time Format Codes

Revision History

| <blockquote><br><p><strong>Revision</strong></p><br></blockquote> | <blockquote><br><p><strong>Date</strong></p><br></blockquote> | <blockquote><br><p><strong>Contents</strong></p><br></blockquote> |
| :--- | :--- | :--- |
| <blockquote><br><p>DRAFT 1.0</p><br></blockquote> | <blockquote><br><p>May 2021</p><br></blockquote> | <blockquote><br><p>Draft release updated for SDMX 3.0 for public consultation</p><br></blockquote> |
| <blockquote><br><p>1.0</p><br></blockquote> | <blockquote><br><p>October 2021</p><br></blockquote> | <blockquote><br><p>Public release for SDMX 3.0</p><br></blockquote> |


Contents

[1 Purpose and Structure
[6](#purpose-and-structure)](#purpose-and-structure)

[1.1 Purpose [6](#purpose)](#purpose)

[1.2 Structure [6](#structure)](#structure)

[2 General Notes on This Document
[7](#general-notes-on-this-document)](#general-notes-on-this-document)

[3 Guide for SDMX Format Standards
[8](#guide-for-sdmx-format-standards)](#guide-for-sdmx-format-standards)

[3.1 Introduction [8](#introduction)](#introduction)

[3.2 SDMX Information Model for Format Implementers
[8](#sdmx-information-model-for-format-implementers)](#sdmx-information-model-for-format-implementers)

[3.2.1 Introduction [8](#introduction-1)](#introduction-1)

[3.3 SDMX Formats: Expressive Capabilities and Function
[8](#sdmx-formats-expressive-capabilities-and-function)](#sdmx-formats-expressive-capabilities-and-function)

[3.3.1 Format Optimizations and Differences
[8](#format-optimizations-and-differences)](#format-optimizations-and-differences)

[3.4 SDMX Best Practices
[10](#sdmx-best-practices)](#sdmx-best-practices)

[3.4.1 Reporting and Dissemination Guidelines
[10](#reporting-and-dissemination-guidelines)](#reporting-and-dissemination-guidelines)

[3.4.2 Best Practices for Batch Data Exchange
[13](#best-practices-for-batch-data-exchange)](#best-practices-for-batch-data-exchange)

[4 General Notes for Implementers
[15](#general-notes-for-implementers)](#general-notes-for-implementers)

[4.1 Representations [15](#representations)](#representations)

[4.1.1 Data Types [17](#data-types)](#data-types)

[4.2 Time and Time Format
[18](#time-and-time-format)](#time-and-time-format)

[4.2.1 Introduction [18](#introduction-3)](#introduction-3)

[4.2.2 Observational Time Period
[18](#observational-time-period)](#observational-time-period)

[4.2.3 Standard Time Period
[18](#standard-time-period)](#standard-time-period)

[4.2.4 Gregorian Time Period
[19](#gregorian-time-period)](#gregorian-time-period)

[4.2.5 Date Time [19](#date-time)](#date-time)

[4.2.6 Standard Reporting Period
[19](#standard-reporting-period)](#standard-reporting-period)

[4.2.7 Distinct Range [22](#distinct-range)](#distinct-range)

[4.2.8 Time Format [23](#time-format)](#time-format)

[4.2.9 Time Zones [23](#time-zones)](#time-zones)

[4.2.10 Representing Time Spans Elsewhere
[24](#representing-time-spans-elsewhere)](#representing-time-spans-elsewhere)

[4.2.11 Notes on Formats [24](#notes-on-formats)](#notes-on-formats)

[4.2.12 Effect on Time Ranges
[24](#effect-on-time-ranges)](#effect-on-time-ranges)

[4.2.13 Time in Query Messages
[24](#time-in-query-messages)](#time-in-query-messages)

[4.3 Versioning [26](#versioning)](#versioning)

[4.3.1 Non-versioned artefacts
[26](#non-versioned-artefacts)](#non-versioned-artefacts)

[4.3.2 Semantically versioned artefacts
[27](#semantically-versioned-artefacts)](#semantically-versioned-artefacts)

[4.3.3 Legacy-versioned artefacts
[28](#legacy-versioned-artefacts)](#legacy-versioned-artefacts)

[4.3.4 Dependency management and references
[28](#dependency-management-and-references)](#dependency-management-and-references)

[4.4 Structural Metadata Querying Best Practices
[29](#structural-metadata-querying-best-practices)](#structural-metadata-querying-best-practices)

[5 Reference Metadata [30](#reference-metadata)](#reference-metadata)

[5.1 Scope of the Metadata Structure Definition (MSD)
[30](#scope-of-the-metadata-structure-definition-msd)](#scope-of-the-metadata-structure-definition-msd)

[5.2 Identification of the Object(s) to which the Metadata is to be
attached
[30](#identification-of-the-objects-to-which-the-metadata-is-to-be-attached)](#identification-of-the-objects-to-which-the-metadata-is-to-be-attached)

[5.3 Metadata Structure Definition
[31](#metadata-structure-definition)](#metadata-structure-definition)

[5.4 Metadata Set [32](#metadata-set)](#metadata-set)

[5.5 Reference Metadata in Data Structure Definition and Dataset
[33](#reference-metadata-in-data-structure-definition-and-dataset)](#reference-metadata-in-data-structure-definition-and-dataset)

[6 Codelist [34](#codelist)](#codelist)

[6.1 Codelist extension and discriminated unions
[34](#codelist-extension-and-discriminated-unions)](#codelist-extension-and-discriminated-unions)

[6.1.1 Prefixing Code Ids
[35](#prefixing-code-ids)](#prefixing-code-ids)

[6.1.2 Including / Excluding Specific Codes
[35](#including-excluding-specific-codes)](#including-excluding-specific-codes)

[6.1.3 Parent Ids [36](#parent-ids)](#parent-ids)

[6.1.4 Discriminated Unions
[38](#discriminated-unions)](#discriminated-unions)

[6.2 Linking Hierarchies
[39](#linking-hierarchies)](#linking-hierarchies)

[7 Geospatial information support
[41](#geospatial-information-support)](#geospatial-information-support)

[7.1 Indirect Reference to Geospatial Information.
[41](#indirect-reference-to-geospatial-information.)](#indirect-reference-to-geospatial-information.)

[7.2 Geographic Coordinates
[42](#geographic-coordinates)](#geographic-coordinates)

[7.3 A Geographic Codelist
[45](#a-geographic-codelist)](#a-geographic-codelist)

[8 Maintenance Agencies and Metadata Providers
[48](#maintenance-agencies-and-metadata-providers)](#maintenance-agencies-and-metadata-providers)

[9 Concept Roles [51](#concept-roles)](#concept-roles)

[9.1 Overview [51](#overview)](#overview)

[9.2 Information Model [51](#information-model)](#information-model)

[9.3 Technical Mechanism
[51](#technical-mechanism)](#technical-mechanism)

[9.4 SDMX-ML Examples in a DSD
[52](#sdmx-ml-examples-in-a-dsd)](#sdmx-ml-examples-in-a-dsd)

[9.5 SDMX standard roles Concept Scheme
[53](#sdmx-standard-roles-concept-scheme)](#sdmx-standard-roles-concept-scheme)

[10 Constraints [55](#constraints)](#constraints)

[10.1 Introduction [55](#introduction-4)](#introduction-4)

[10.2 Types of Constraint
[55](#types-of-constraint)](#types-of-constraint)

[10.3 Rules for a Constraint
[56](#rules-for-a-constraint)](#rules-for-a-constraint)

[10.3.1 Scope of a Constraint
[56](#scope-of-a-constraint)](#scope-of-a-constraint)

[10.3.2 Multiple Constraints
[57](#multiple-constraints)](#multiple-constraints)

[10.3.3 Inheritance of a Constraint
[58](#inheritance-of-a-constraint)](#inheritance-of-a-constraint)

[10.3.4 Constraints Examples
[59](#constraints-examples)](#constraints-examples)

[11 Transforming between versions of SDMX
[67](#transforming-between-versions-of-sdmx)](#transforming-between-versions-of-sdmx)

[11.1 Scope [67](#scope)](#scope)

[11.2 Compatibility and new DSD features
[67](#compatibility-and-new-dsd-features)](#compatibility-and-new-dsd-features)

[12 Validation and Transformation Language (VTL)
[68](#validation-and-transformation-language-vtl)](#validation-and-transformation-language-vtl)

[12.1 Introduction [68](#introduction-5)](#introduction-5)

[12.2 References to SDMX artefacts from VTL statements
[69](#references-to-sdmx-artefacts-from-vtl-statements)](#references-to-sdmx-artefacts-from-vtl-statements)

[12.2.1 Introduction [69](#introduction-6)](#introduction-6)

[12.2.2 References through the URN
[69](#references-through-the-urn)](#references-through-the-urn)

[12.2.3 Abbreviation of the URN
[71](#abbreviation-of-the-urn)](#abbreviation-of-the-urn)

[12.2.4 User-defined alias
[74](#user-defined-alias)](#user-defined-alias)

[12.2.5 References to SDMX artefacts from VTL Rulesets
[74](#references-to-sdmx-artefacts-from-vtl-rulesets)](#references-to-sdmx-artefacts-from-vtl-rulesets)

[12.3 Mapping between SDMX and VTL artefacts
[75](#mapping-between-sdmx-and-vtl-artefacts)](#mapping-between-sdmx-and-vtl-artefacts)

[12.3.1 When the mapping occurs
[75](#when-the-mapping-occurs)](#when-the-mapping-occurs)

[12.3.2 General mapping of VTL and SDMX data structures
[76](#general-mapping-of-vtl-and-sdmx-data-structures)](#general-mapping-of-vtl-and-sdmx-data-structures)

[12.3.3 Mapping from SDMX to VTL data structures
[76](#mapping-from-sdmx-to-vtl-data-structures)](#mapping-from-sdmx-to-vtl-data-structures)

[12.3.4 Mapping from VTL to SDMX data structures
[79](#mapping-from-vtl-to-sdmx-data-structures)](#mapping-from-vtl-to-sdmx-data-structures)

[12.3.5 Declaration of the mapping methods between data structures
[82](#declaration-of-the-mapping-methods-between-data-structures)](#declaration-of-the-mapping-methods-between-data-structures)

[12.3.6 Mapping dataflow subsets to distinct VTL Data Sets
[83](#mapping-dataflow-subsets-to-distinct-vtl-data-sets)](#mapping-dataflow-subsets-to-distinct-vtl-data-sets)

[12.3.7 Mapping variables and value domains between VTL and SDMX
[88](#mapping-variables-and-value-domains-between-vtl-and-sdmx)](#mapping-variables-and-value-domains-between-vtl-and-sdmx)

[12.4 Mapping between SDMX and VTL Data Types
[90](#mapping-between-sdmx-and-vtl-data-types)](#mapping-between-sdmx-and-vtl-data-types)

[12.4.1 VTL Data types [90](#vtl-data-types)](#vtl-data-types)

[12.4.2 VTL basic scalar types and SDMX data types
[92](#vtl-basic-scalar-types-and-sdmx-data-types)](#vtl-basic-scalar-types-and-sdmx-data-types)

[12.4.3 Mapping SDMX data types to VTL basic scalar types
[93](#mapping-sdmx-data-types-to-vtl-basic-scalar-types)](#mapping-sdmx-data-types-to-vtl-basic-scalar-types)

[12.4.4 Mapping VTL basic scalar types to SDMX data types
[95](#mapping-vtl-basic-scalar-types-to-sdmx-data-types)](#mapping-vtl-basic-scalar-types-to-sdmx-data-types)

[12.4.5 Null Values [97](#null-values)](#null-values)

[12.4.6 Format of the literals used in VTL Transformations
[98](#format-of-the-literals-used-in-vtl-transformations)](#format-of-the-literals-used-in-vtl-transformations)

[13 Structure Mapping [99](#structure-mapping)](#structure-mapping)

[13.1 Introduction [99](#introduction-7)](#introduction-7)

[13.2 1-1 structure maps [99](#structure-maps)](#structure-maps)

[13.3 N-n structure maps
[100](#n-n-structure-maps)](#n-n-structure-maps)

[13.4 Ambiguous mapping rules
[101](#ambiguous-mapping-rules)](#ambiguous-mapping-rules)

[13.5 Representation maps
[101](#representation-maps)](#representation-maps)

[13.6 Regular expression and substring rules
[102](#regular-expression-and-substring-rules)](#regular-expression-and-substring-rules)

[13.6.1 Regular expressions
[103](#regular-expressions)](#regular-expressions)

[13.6.2 Substrings [103](#substrings)](#substrings)

[13.7 Mapping non-SDMX time formats to SDMX formats
[104](#mapping-non-sdmx-time-formats-to-sdmx-formats)](#mapping-non-sdmx-time-formats-to-sdmx-formats)

[13.7.1 Pattern based dates
[105](#pattern-based-dates)](#pattern-based-dates)

[13.7.2 Numerical based datetime
[108](#numerical-based-datetime)](#numerical-based-datetime)

[13.7.3 Mapping more complex time inputs
[109](#mapping-more-complex-time-inputs)](#mapping-more-complex-time-inputs)

[13.8 Using TIME\_PERIOD in mapping rules
[109](#using-time_period-in-mapping-rules)](#using-time_period-in-mapping-rules)

[13.9 Time span mapping rules using validity periods
[109](#time-span-mapping-rules-using-validity-periods)](#time-span-mapping-rules-using-validity-periods)

[13.10 Mapping examples [110](#mapping-examples)](#mapping-examples)

[13.10.1 Many to one mapping (N-1)
[110](#many-to-one-mapping-n-1)](#many-to-one-mapping-n-1)

[13.10.2 Mapping other data types to Code Id
[110](#mapping-other-data-types-to-code-id)](#mapping-other-data-types-to-code-id)

[13.10.3 Observation Attributes for Time Period
[111](#observation-attributes-for-time-period)](#observation-attributes-for-time-period)

[13.10.4 Time mapping [111](#time-mapping)](#time-mapping)

[14 ANNEX Semantic Versioning
[113](#annex-semantic-versioning)](#annex-semantic-versioning)

[14.1 Introduction to Semantic Versioning
[113](#introduction-to-semantic-versioning)](#introduction-to-semantic-versioning)

[14.2 Semantic Versioning Specification for SDMX 3.0(.0)
[113](#semantic-versioning-specification-for-sdmx-3.0.0)](#semantic-versioning-specification-for-sdmx-3.0.0)

[14.3 Backus–Naur Form Grammar for Valid SDMX 3.0(.0) Semantic Versions
[115](#backusnaur-form-grammar-for-valid-sdmx-3.0.0-semantic-versions)](#backusnaur-form-grammar-for-valid-sdmx-3.0.0-semantic-versions)

[14.4 Dependency Management in SDMX 3.0(.0):
[116](#dependency-management-in-sdmx-3.0.0)](#dependency-management-in-sdmx-3.0.0)

[14.5 Upgrade and conversions of artefacts defined with previous SDMX
standard versions to Semantic Versioning
[117](#upgrade-and-conversions-of-artefacts-defined-with-previous-sdmx-standard-versions-to-semantic-versioning)](#upgrade-and-conversions-of-artefacts-defined-with-previous-sdmx-standard-versions-to-semantic-versioning)

[14.6 FAQ for Semantic Versioning
[118](#faq-for-semantic-versioning)](#faq-for-semantic-versioning)