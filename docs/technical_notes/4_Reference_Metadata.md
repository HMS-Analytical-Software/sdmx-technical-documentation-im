# Reference Metadata

## Scope of the Metadata Structure Definition (MSD)

The scope of the MSD is reduced in SDMX 3.0, by means of simplifying its
structure, but also in the way referenced Artefacts are targeted. In
fact, the MSD is restricted to play the role of a single container,
without targeting any specific Artefact. The possible targets of
Metadata Set are specified in the Metadataflows or Metadata Provision
Agreements relating to that MSD. To achieve that, the structure of the
Metadataflow has changed in this version of the standard. Moreover, the
Metadata Provision Agreement Artefact is introduced to include this
feature.

Two more changes, introduced in this version, are the following:

-   The Metadata Set becomes a Maintainable Artefact but maintained by a
    Metadata Provider (another new Artefact in this version).

-   Metadata Attributes may also be used in Data Structure Definitions,
    as long as the latter reference the Metadata Structure Definition
    that specify those Metadata Attributes.

## Identification of the Object(s) to which the Metadata is to be attached

The following example shows the structure and naming of the MSD and
related components for creating reference metadata.

The schematic structure of an MSD is shown below.

![](media/image2.png)

Figure 1: Schematic of the Metadata Structure Definition

The MSD contains one Metadata Attribute Descriptor comprising the
Metadata Attributes that identify the Concepts for which metadata may be
reported in the Metadata Set. The Metadataflow and Metadata Provision
Agreement comprise the specification of the objects to which metadata
can be reported in a Metadata Set (Metadata Target(s)).

The high-level view of the MSD, as well as the way the Metadataflow and
Metadata Provision Agreement specify the Targets:

**&lt;str:MetadataStructure agencyID="SDMX" id="MSD"
version="1.0.0-draft"&gt;  
&lt;com:Name&gt;MSD 3.0 sample&lt;/com:Name&gt;  
&lt;str:MetadataAttributeDescriptor
id="MetadataAttributeDescriptor"&gt;  
...  
&lt;/str: MetadataAttributeDescriptor&gt;  
&lt;/str:MetadataStructure&gt;**

Figure 2: The high-level view of the MSD containing one Metadata
Attribute Descriptor

**&lt;str:Metadataflow agencyID="OECD" id="GENERAL\_METADATA"
version="1.0.0-draft"&gt;  
&lt;com:Name xml:lang="en"&gt;Metadataflow 3.0 sample&lt;/com:Name&gt;  
&lt;str:Structure&gt;urn:sdmx:org.sdmx.infomodel.metadatastructure.**

**MetadataStructure=OECD:MSD(1.0.0-draft)&lt;/str:Structure&gt;**

**&lt;!-- Attach to any Dataflows maintained by the OECD --&gt;  
&lt;str:Targets&gt;urn:sdmx:org.sdmx.infomodel.datastructure.**

**Dataflow=OECD:\*(\*)&lt;/str:Targets&gt;  
&lt;/str:Metadataflow&gt;**

Figure 3: Wildcarded Target Objects as specified in a Metadataflow

**&lt;str:MetadataProvisionAgreement agencyID="OECD"
id="ABS\_INDICATORS" version="1.0.0-draft"&gt;  
&lt;com:Name xml:lang="en"&gt;Metadata Provision Agreement 3.0
sample&lt;/com:Name&gt;  
&lt;str:StructureUsage&gt;urn:sdmx:org.sdmx.infomodel.metadatastructure.**

**Metadataflow=OECD:GENERAL\_METADATA(1.0.0-draft)&lt;/str:StructureUsage&gt;  
&lt;str:MetadataProvider&gt;urn:sdmx:org.sdmx.infomodel.base.**

**MetadataProvider=OECD:METADATA\_PROVIDERS(1.0).ABS&lt;/str:MetadataProvider&gt;**

**&lt;!-- Attach to specific Dataflows maintained by the OECD --&gt;  
&lt;str:Target&gt;urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=**

**OECD:GDP(\*)&lt;/str:Target&gt;**

**&lt;str:Target&gt;urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=**

**OECD:EXR(\*)&lt;/str:Target&gt;**

**&lt;str:Target&gt;urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=**

**OECD:ABC(\*)&lt;/str:Target&gt;  
&lt;/str:MetadataProvisionAgreement&gt;**

Figure 4: Specific Target Objects as specified in a Metadata Provision
Agreement

Note that the SDMX-ML schemas have specific XML elements for each
identifiable object type because identifying, for instance, a
Maintainable Object has different properties from an Identifiable Object
which must also include the agencyId, version, and id of the
Maintainable Object in which it resides.

## Metadata Structure Definition

An example is shown below.

**&lt;str:MetadataStructure agencyID="SDMX" id="MSD"
version="1.0.0-draft"&gt;  
&lt;com:Name&gt;MSD 3.0 sample&lt;/com:Name&gt;  
&lt;str:MetadataAttributeDescriptor
id="MetadataAttributeDescriptor"&gt;  
&lt;str:MetadataAttribute id="CONTACT" isPresentational="true"&gt;  
&lt;str:ConceptIdentity&gt;urn:sdmx:org.sdmx.infomodel.conceptscheme.**

**Concept=SDMX:CONCEPTS(1.0.0).CONTACT&lt;/str:ConceptIdentity&gt;  
&lt;str:MetadataAttribute id="CONTACT\_NAME" minOccurs="1"
maxOccurs="1"&gt;  
&lt;str:ConceptIdentity&gt;urn:sdmx:org.sdmx.infomodel.conceptscheme.**

**Concept=SDMX:CONCEPTS(1.0.0).CONTACT\_NAME&lt;/str:ConceptIdentity&gt;  
&lt;str:LocalRepresentation&gt;  
&lt;str:TextFormat textType="String"/&gt;  
&lt;/str:LocalRepresentation&gt;  
&lt;/str:MetadataAttribute&gt;  
&lt;str:MetadataAttribute id="ADDRESS" minOccurs="1" maxOccurs="3"
isPresentational="true"&gt;  
&lt;str:ConceptIdentity&gt;urn:sdmx:org.sdmx.infomodel.conceptscheme.**

**Concept=SDMX:CONCEPTS(1.0.0).ADDRESS&lt;/str:ConceptIdentity&gt;  
&lt;str:MetadataAttribute id="HOUSE\_NUMBER" minOccurs="1"
maxOccurs="1"&gt;  
&lt;str:ConceptIdentity&gt;urn:sdmx:org.sdmx.infomodel.conceptscheme.**

**Concept=SDMX:CONCEPTS(1.0.0).HOUSE\_NUMBER&lt;/str:ConceptIdentity&gt;  
&lt;str:LocalRepresentation&gt;  
&lt;str:TextFormat textType="Integer"/&gt;  
&lt;/str:LocalRepresentation&gt;  
&lt;/str:MetadataAttribute&gt;  
&lt;/str:MetadataAttribute&gt;  
&lt;/str:MetadataAttribute&gt;  
&lt;/str:MetadataAttributeDescriptor&gt;  
&lt;/str:MetadataStructure&gt;**

Figure 5: Example MSD showing specification of some Metadata Attributes

This example shows the following hierarchy of Metadata Attributes:

-   Contact – this is presentational; no metadata is expected to be
    reported at this level

    -   Contact Name

    -   Address – this is also presentational; up to 3 addresses are
        allowed

        -   House Number

## Metadata Set

An example of reporting metadata according to the MSD described above,
is shown below.

**&lt;msg:MetadataSet id="ALB" metadataProviderID="OECD"
version="1.0.0"&gt;  
&lt;str:MetadataProvision&gt;urn:sdmx:org.sdmx.infomodel.registry.MetadataProvisionAgreement=OECD:ABS\_INDICATORS(1.0.0-draft)&lt;/str:MetadataProvision&gt;  
&lt;str:Target&gt;urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=OECD:GDP(1.0.0)&lt;/str:Target&gt;  
&lt;md:AttributeSet&gt;  
&lt;md:ReportedAttribute id="CONTACT"&gt;  
&lt;md:AttributeSet&gt;  
&lt;md:ReportedAttribute id="CONTACT\_NAME"&gt;John Doe**

**&lt;/md:ReportedAttribute&gt;  
&lt;md:ReportedAttribute id="ADDRESS"&gt;  
&lt;md:AttributeSet&gt;  
&lt;md:ReportedAttribute id="STREET\_NAME"&gt;  
&lt;com:Text xml:lang="en"&gt;5th Avenue&lt;/com:Text&gt;  
&lt;/md:ReportedAttribute&gt;  
&lt;md:ReportedAttribute id="HOUSE\_NUMBER"&gt;12**

**&lt;/md:ReportedAttribute&gt;  
&lt;/md:AttributeSet&gt;  
&lt;/md:ReportedAttribute&gt;  
&lt;md:ReportedAttribute id="HTML\_ATTR"&gt;  
&lt;com:StructuredText xml:lang="en"&gt;  
&lt;div xmlns="http://www.w3.org/1999/xhtml"&gt;  
&lt;p&gt;Lorem Ipsum&lt;/p&gt;  
&lt;/div&gt;  
&lt;/com:StructuredText&gt;  
&lt;/md:ReportedAttribute&gt;  
&lt;/md:AttributeSet&gt;  
&lt;/md:ReportedAttribute&gt;  
&lt;/md:AttributeSet&gt;**

**&lt;/msg:MetadataSet&gt;**

Figure 6: Example Metadata Set

This example shows:

1.  The reference to the Metadata Provision Agreement and Metadata
    Target

2.  The reported metadata attributes (AttributeSet)

## Reference Metadata in Data Structure Definition and Dataset

An important change of SDMX 3.0 is the ability to reference an MSD
within a DSD, in order to report any Metadata Attributes defined in the
former to Datasets of the latter. This is achieved by the following:

-   In a DSD, the user may add a reference to one MSD.

-   In the Attribute Descriptor of the DSD, the user may include any
    Metadata Attributes defined in the linked MSD.

    -   For each link to a Metadata Attribute, an Attribute Relationship
        may be specified (similarly to that for Data Attributes).

-   In any Dataset complying with this DSD, Metadata Attributes may be
    reported according to the specified Attribute Relationship.

    -   The hierarchy of the Metadata Attributes defined in the MSD must
        be respected and they are reported in the same way as in a
        Metadataset, under the level they are related within the DSD,
        via their Attribute Relationship.

-   In Data Constraints, the user is allowed to restrict values for
    Metadata Attributes, in the same way as Data Attributes (more on
    this in section “10 Constraints”).