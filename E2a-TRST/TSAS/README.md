# Test Instruction Template

| Documentation Code   | Title                                          | Exchange Code | Test Code | Author          | Data Owner | Version | Date       |
|----------------------|------------------------------------------------|---------------|-----------| ----------------|------------|---------|------------|
| IFC4.3AbRV_E2a_TSAS  | Track Structures Advanced Sweeps               | E2a-TRST      | TSAS      |                 |            | 1.0     | 28.03.2022 |


## Summary (Intent)

This test instruction is defined for IFC4.3AbRV_E2a_TSAS Track Structures Advanced Sweeps.

It covers following subjects:
- A basic project structure setup including units, context and global positioning
- One alignment for a section of railway, including the horizontal, vertical and cant layouts
- One rail as a sweep of the IfcSegmentedReferenceCurve (representing the cant layout) and one rail as a sweep of an IfcOffsetCurveByDistances based on the same IfcSegmentedReferenceCurve.
- Swept area solid geometry of the base represented by IfcSectionedSolidHorizontal

The [Expected Results](#Expected-Results) section lists the material that will be used to assess the fulfilment of capabilities.

:zap: **This is a test-driven process: refer to the [Validation Criteria](#Validation-Criteria) to understand what is required by the test** :zap:

## Itemised Roots

The Test instruction addresses the import and export of the following IFC Entities & Concept Templates:

<details><summary>IFC Entities</summary>

These entities represent a test-specific subset of the wider AbRV_Ex exchange and the overall AbRV MVD. **The scope of the test shall not be used as a definitive scope of the exchange, or of the entire MVD.**

- *Rooted Entities*
  - *IfcProject*
  - *IfcSite*
  - *IfcAlignment*
  - *IfcAlignmentSegment*
  - *IfcAlignmentHorizontal*
  - *IfcAlignmentVertical*
  - *IfcAlignmentCant*
  - *IfcBuiltElement*
  
- *Curves*
  - *IfcGradientCurve*
  - *IfcSegmentedReferenceCurve*
  - *IfcOffsetCurveByDistances*

</details>

<details><summary>Concept Templates</summary>

These concept templates represent a test-specific subset of the wider AbRV_Ex exchange and the overall AbRV MVD, that must be correctly exported to meet the validation criteria. **The scope of the test shall not be used as a definitive scope of the exchange, or of the entire MVD.**

- *Optional Grouping*
  - *Project Units*
  - *Project Representation Context*
  - *Spatial Decomposition*
  - *Spatial Composition*
  - *Spatial Container*
  - *Spatial Containment*
  - *Alignment Layout*
  - *Alignment Geometry Gradient*
  - *Alignment Geometry Cant*
  - *Axis Geometry*
  - *Body AdvancedSwept Directrix Geometry*
  - *Body SectionedSolidHorizontal*
 
</details>

## Test Case Imports
Test instructions are defined with a modular approach to reduce repetition of validation criteria and test content, and improve vendors ability to solve issues and bugs. therefore this test instruction *imports/reuses* the following Test instructions and entities with the relevant associated validation criteria.

<details><summary>Imports & Reuses</summary>

| TI Code                                  | Test Instruction Title    | Comments                     |
|------------------------------------------|---------------------------|------------------------------|
| [IFC4.3AbRV_E0_MSTP](../../E0-SCFD/MSTP) | Model Setup & Positioning | PROJ-01 imported along with RCTX-01 and associated configuration and history data |

</details>

## Usages, Constraints & Logic
The following itemised restrictions and constraints shall be placed on IFC Entities & Concept Templates:

<details><summary>Semantic Usages, Constraints & Logic</summary>


</details>

<details><summary>Model Geometry</summary>
The Test case requires the following additional checks related to Model Geometry:

The geometry should contain three individual sweeps, i.e.:
- Right Rail
- Left Rail
- Base

Right Rail
The right rail should be modelled using a sweep directly on the IfcSegmentedReferencCurve. The structure should look like:
- IfcDirectrixDerivedReferenceSweptAreaSolid
  - Directrix
    - IfcSegmentedReferenceCurve
  - SweptArea
    - IfcDerivedProfileDef
      - ParentProfile
        - IfcArbitraryClosedProfileDef
      - Operator
        - IfcCartesianTransformationOperator2D => translation + rotation
  - FixedReference
    - IfcDirection (0., 0., 1.)

Left Rail
The left rail should be modelled using a sweep based on an offset curve. The structure should look like:
- IfcDirectrixDerivedReferenceSweptAreaSolid
  - Directrix
    - IfcOffsetCurveByDistances
      - BasisCurve
        - IfcSegmentedReferenceCurve
      - OffsetValues
        - IfcPointByDistanceExpression => translation
  - SweptArea
    - IfcDerivedProfileDef
      - ParentProfile
        - IfcArbitraryClosedProfileDef
      - Operator
        - IfcCartesianTransformationOperator2D => rotation
  - FixedReference
    - IfcDirection (0., 0., 1.)
 
Base
The base should be defined by a sectioned solid sweep. The structure should look like:
- IfcSectionedSolidHorizontal
  - Directrix
    - IfcSegmentedReferenceCurve
  - CrossSections
    - IfcDerivedProfileDef
      - ParentProfile
        - IfcArbitraryClosedProfileDef (the profile as defined in figure 5)
      - Operator
        - IfcCartesianTransformationOperator2D => rotation based on segment
  - CrossSectionPositions
    - IfcAxis2PlacementLinear (at the start of each Cant Alignment Segment and at the end of the IfcSegmentedReferenceCurve)
  
</details>

## Expected Results

For certification of capabilities the only source will be:

- n. 1 IFC file containing the information as requested. The file shall be named using the following syntax: `MVDCode`-`ExchangeCode`-`TestCode`-`SoftwareVendor`.`ifc` (Example: `IFC4.3_AbRV-E2b-ASTPC-AmazingSoft.ifc`)

Considering the aim of this test, other **optional** results, not subject to the bSI certification process, yet useful to illustrate test results are:
- Screen-shot of ...
- CSV export of ...

---

## Validation criteria
:zap: For this test case to be considered passed **all capabilities** listed in this section shall be verified, with no exception. :zap:

### General & Imports

<details><summary>Click to expand</summary>

- All the concept templates must be correctly implemented as presented in the validation criteria
- At least 1 instance of each entity listed in [Itemised Roots](#Itemised-Roots) is present in the file.


#### Imports
| **TI Code**        | **Criteria Codes** | *COMMENT**                                         |
|--------------------|--------------------|----------------------------------------------------|
| IFC4.3AbRV_E0_MSTP | ALL CRITERIA       | As outlined in the dataset [Imported Entities Table](Dataset/README.md#Imported-Entities-Table) |


#### General
| **ID**  | **CRITERIA**                                        | **VALUE**                                     | **COMMENT** |
|---------|-----------------------------------------------------|-----------------------------------------------|-------------|
| GENE_01 | All requested entities are present in the IFC model | per [Entities Table](Dataset/README.md#Entities-Table) |    |

</details>

### Product geometric representation

| **RULE ID** | **CRITERIA**                            | **VALUE [examples]**                     | **ENTITY (if applicable)** | **CT (if applicable)**     |
|-------------|-----------------------------------------|------------------------------------------|----------------------------|----------------------------|
| PREP_01     | Geometric representation of products is verified | As per Product Geometric Representation Table |                   | Product Geometric Representation and its subtemplates |

> **Acceptance criteria**: For the **Group Geometric Representation** capability, the validation procedure must verify that a Product of the requested type (and optionally a requested name) has an IfcShapeRepresentation with the requested Representation Identifier, Representation Type and Items.

<details><summary>PREP_01 details:  Geometric representation of products is verified</summary>

> - Given a set of products taken from the [Product Geometric Representation Table](#Product-Geometric-Representation-Table)
> - Then the Product, and optionally the Product Type, exists
> - And the Product must have an IfcShapeRepresentation (via IfcProductDefinitionShape) with the requested Representation Identifier, Representation Type and Items.

</details>
