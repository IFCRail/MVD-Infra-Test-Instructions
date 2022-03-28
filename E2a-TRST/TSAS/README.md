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

:construction: under construction :construction:

<details><summary>Imports & Reuses</summary>

| TI Code                                  | Test Instruction Title    | Comments                     |
|------------------------------------------|---------------------------|------------------------------|
| [IFC4.3AbRV_E0_MSTP](../../E0-SCFD/MSTP) | Model Setup & Positioning | PROJ-01 imported along with RCTX-01 and associated configuration and history data |

</details>

## Usages, Constraints & Logic
The following itemised restrictions and constraints shall be placed on IFC Entities & Concept Templates:

:construction: under construction :construction:

<details><summary>Semantic Usages, Constraints & Logic</summary>

The following itemised Usages, Constraints & Logic are normative entries within the AbRV MVD and MUST be satisfied to meet the defined validation criteria

- IfcSomething
    - *Constraint*

</details>

<details><summary>Model Geometry</summary>
The Test case requires the following additional checks related to Model Geometry:

- *Constraint*

</details>

## Expected Results

For certification of capabilities the only source will be:

:construction: under construction :construction:

- n. 1 IFC file containing the information as requested. The file shall be named using the following syntax: `MVDCode`-`ExchangeCode`-`TestCode`-`SoftwareVendor`.`ifc` (Example: `IFC4.3_AbRV-E2b-ASTPC-AmazingSoft.ifc`)

Considering the aim of this test, other **optional** results, not subject to the bSI certification process, yet useful to illustrate test results are:
- Screen-shot of ...
- CSV export of ...

---

## Validation criteria
:zap: For this test case to be considered passed **all capabilities** listed in this section shall be verified, with no exception. :zap:

:construction: under construction :construction:

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

### Some Concept Group

<details><summary>Click to expand</summary>
Criteria around the representation of 'Some Concept'

| **ID**  | **CRITERIA**                                        | **VALUE**                                | **COMMENT** |
|---------|-----------------------------------------------------|------------------------------------------|-------------|
| XXXX_01 | A Criteria to follow                               | its expected value or outcome            |             |

</details>
