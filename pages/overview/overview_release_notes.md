---
title: Release Notes
keywords: development, versioning
tags: [development]
sidebar: overview_sidebar
permalink: overview_release_notes.html
summary: Summary release notes of the versions released in ITK3 eDischarge Implementation Guide
---

## 2.5.0-Release Candidate ##

**General Page Issues**

- Fixed broken links to CareConnect Profiles.
- Fixed display issues with section pages displaying random ## characters

**Profiles** 


- All Profiles are now "Active" status
- Condition Profile has optional condition.note added to profile and minor version increased +1
- Composition Profile has care-setting extension aligned with CareConnect results in a URL change but structure is identical
- Composition Profile has document type value set aligned with CareConnect results in URL change but codes are identical
- Composition Profile, Medical and medical devices section entry cardinally change from 1..* to 0..* to allow for when medication cannot be coded    
- Removal of Organization reference from Person Completing record Section as it was an incorrect reference
- Removal of optional element verificationStatus from Composition Profile as no requirement to use for Transfer of Care
- MedicationDispense Profile Identifier.system and Identifier.value cardinality changed from 0..1 to 1..1. to align with MVP document 
- CareConnect-ITK-AllergyIntolerance-1 added optional SNOMED CT Description Id extension to AllergyIntolerance.code element not used by ToC but added to future proof ITK Profiles
- CareConnect-ITK-AllergyIntolerance-1 Profile AllergyIntolerance.assertedDate element cardinality changed from 0..1 to 1..1. to align with MVP document and CareConnect base Profile 

**Care Connect Profiles Changes that Impact ToC**
- CareConnnect Profiles are now the latest "Active" versions minor version is increased +1 these are minor changes with very little impact on Toc known impact is listed in this change history

**CareConnect Value Set Changes that Impact ToC**
- CareConnect-ListCode-1 value set display value="Allergies and adverse reaction" should be display value="Allergies and adverse reactions".
- null flavor codes added to the ValueSet CareConnect-AllergyManifestation-1 used in element AllergyIntolerance.reaction.manifestation

**PRSB Headings**

- Specification has been aligned with the latest PRSB maintenance release
- Organisation name element in Distribution List section changed from optional to required
- Probability of recurrence element removed from Allergies and Adverse Reactions section

**Vale Sets**

- See CareConnect Value Set 

**Message Definitions**

- Updated to reflect changes to FHIR asset versions due to changes documented here.
- Message definition URL aligned with NHS Digital FHIR policy naming by removing word instance

**Additional Guidance**

- Added guidance for population of GP Practice identifier(ODS Code) when using MESH look up [see](build_mesh.html#use-of-gp-look-up-on-mesh)
- Added guidance for document replacement semantics [see](build_replacement.html#fhir-elements-used-for-replacement)  

**Diagrams**

- Section overview diagram updated to remove reference to organization on Person Completing Record section

## 2.4.0-beta ##

**Profiles**

- New CareConnect-ITK-MedicationResponse-1 Profile added to support TTOs (To take outs)
- Updated CareConnect-ITK-MedicationStatement-1 to support reference to CareConnect-ITK-MedicationResponse-1.

**Specification Pages**

- Updated Profile page to include the new Profile
- Updated Message Definitions
- Added new MedicationDispense referencing diagram
- Updated MedicationStatement referencing diagram to include MedicationDispense Resource
- Update "Build medication list" pages 

## 2.3.0-beta ##

**PRSB section tables** 

These have been updated to include mappings of the PRSB elements to the FHIR elements (where there are mappings). 

**Examples**

Examples have been updated and corrected following further validation.

All Coded entries are now done as lists. Medication is now two lists one for "Active" and one for "Discontinued". 

**Constructing clinical coded structures section**

Updated with new guidance derived from INTEROPen curation.

## 2.2.0-alpha ##

**Profiles**

All profiles have been updated to align with CareConnect profiles following INTEROPen curation.

**Examples**
All examples have been updated to align with CareConnect profiles following INTEROPen curation.

**Section**

The section Design & Build/Constructing Clinical Coded Structures has been updated to reflect the change to the approach following 
INTEROPen curation process.

## 2.1.0-alpha ##

**Infrastructure Changes**

Changed to align with the ITK3 Messaging Distribution specification version 2.1.0-beta.  

**Messaging Architecture Changes**

Interactions have been replaced by message definitions and new ITK3 Handling keys.

**Value sets / Code Systems**

The url for ValueSet-CareSettingType-1, has changed to <https://fhir.nhs.uk/STU3/ValueSet/CareSettingType-1> so that it can be used across programs, also the internal version has changed to 1.0.0.

**Composition Sections**

The structure used for the Patient demographics , GP practice and Distribution list sections has been changed to have specific slices in the composition to align with all other PRSB sections. Descriptions and examples have been updated to suit.

**Section Guidance**

All PRSB headings and subheadings have been updated following release of the version 1.0 Final PRSB documentation. Descriptions and examples have been updated to suit. 

**New Profiles**

Added Binary Resource Profile to allow support for attachments.

**Specification Structure**

Added new sub menus under Design and build section for "Use of Attachments" and "Rendering of Documents" these are place-holders for guidance to be issued in a later release.

## 2.0.0-alpha.1 ##
First version published using Jekyll

