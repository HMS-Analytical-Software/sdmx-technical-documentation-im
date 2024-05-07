# Content Constraint reverse the reference from Constraint to Constrained

## Overview
Currently a Constraint references which structure(s) it is constraining. 

The proposal is to reverse the reference, so it is (for example) the Dataflow that references the Constraint and not the other way round.

## Example
Based on the following Data Constraint
https://registry.sdmx.org/sdmx/v2/structure/dataconstraint/ESTAT/CR_BPM6_BOP_M/2.1

In SDMX v3.0.0 (current) the Constraint has

    Agency     : ESTAT
    Id         : CR_BPM6_BOP_M
    Version    : 2.1
    CubeRegion : (rules go here)
    ConstraintAttachment
      urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=ESTAT:BPM6_BOP_M(2.2)
      urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=ESTAT:BPM6_BOP_M(2.1)

  
With the Corresponding Dataflows 

    Agency  : ESTAT
    Id      : CR_BPM6_BOP_M
    Version : 2.1
    DSD     : urn:sdmx:org.sdmx.infomodel.datastructure.DataStructure=IMF:BOP(2.1)
  
    Agency  : ESTAT
    Id      : CR_BPM6_BOP_M
    Version : 2.2
    DSD     : urn:sdmx:org.sdmx.infomodel.datastructure.DataStructure=IMF:BOP(2.2)


In SDMX v3.1.0 (proposed) the Constraint has

    Agency     : ESTAT
    Id         : CR_BPM6_BOP_M
    Version    : 2.1
    CubeRegion : (rules go here)
  
With the Corresponding Dataflows 

    Agency     : ESTAT
    Id         : CR_BPM6_BOP_M
    Version    : 2.1
    DSD        : urn:sdmx:org.sdmx.infomodel.datastructure.DataStructure=IMF:BOP(2.1)
    Constraint : urn:sdmx:org.sdmx.infomodel.registry.DataConstraint=ESTAT:CR_BPM6_BOP_M(2.1)
  
    Agency     : ESTAT
    Id         : CR_BPM6_BOP_M
    Version    : 2.2
    DSD        : urn:sdmx:org.sdmx.infomodel.datastructure.DataStructure=IMF:BOP(2.2)
    Constraint : urn:sdmx:org.sdmx.infomodel.registry.DataConstraint=ESTAT:CR_BPM6_BOP_M(2.1)
  
Note how more then one Dataflow can references the same Constraint.  

## Impact

If using an SDMX 3.1.0 SDMX Structure Repository which can handle previous versions of SDMX, like the FMR, the tool should support both models and therefore the following applies: 

#### Output Formats

The reference moves to the correct structure based on the version of the output.  This means each output format is syntactically correct with respect to it respective schema.  This allows applications to continue working as they did without change. 

##### Examples 

**Note** Dataflows are used in the examples but it could be any constrainable structure, including Data Provider, DSD, Dataflow, Provision Agreement

    When exporting the Constraint in version 3.1.0 it will no longer contain the Dataflow Reference. 
    When exporting the Dataflow in version 3.1.0 it will (or may) reference the Constraint.
    
    When exporting the Constraint in version 3.0.0 (or lower) it will contain the Dataflow Reference(s)
    When exporting the Dataflow in version 3.0.0 (or lower) it will not reference a Constraint.  

#### REST API

When querying for structures via the SDMX REST API, the behaviour will be in keeping with the requested output version.  This means an application using the REST API to query for Constraints and Dataflows will not need to change if they continue to use SDMX v3.0.0 or lower.

##### Examples

    Query for Constraint in version 3.0.0 with references=descendants will include Dataflow(s).
    Query for Constraint in version 3.1.0 with references=descendants will not include Dataflow(s) - but references=parents will

    Query for Dataflow in version 3.0.0 with references=descendants will not include the Constraint - but references=parents will.
    Query for Dataflow in version 3.1.0 with references=descendants will include Constraint (if one is used).

#### Semantic Verisoning

A decision would have to be made regarding this.

If the Constraint is submitted in version 3.0.0 which uses semantic versioning to reference a Dataflow, should (and if so how) this information be retained when moving this reference to 3.1.0 Dataflow(s). 

 



