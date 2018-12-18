---
title: Birth Details Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_birth_details_used.html
summary: "The FHIR profiles used for the Birth Details Event Message Bundle"
---

The following FHIR profiles are used to form the Birth Details Event Message Bundle:

- [NHSD-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [NHSD-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH005 - Birth Details' XXXXXXXXXXXXXXX
- [CareConnect-NHSD-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [NHSD-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-NHSD-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-NSHD-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1) - where the type element is represented using Child Health Encounter type '003 - Birth' XXXXXXXXXXXXXXXX
- [CareConnect-NHSD-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PhysicalProblemAtBirth-Condition-1)
- [CareConnect-NHSD-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-APGARScore-Observation-1)
- [CareConnect-NHSD-Procedure-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-NeonatalResuscitationMethod-Procedure-1)
- [CareConnect-NHSD-Location-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Delivery-Location-1)

## Birth Details Event data item mapping to FHIR profiles ##

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

Bundle Resource Implementation

## Mapping for Bundle ##

|-|Level 1|Bundle Resource|->|Level 2| None|- - ->|Level 3|NHSD-Bundle-1 Profile|

|[View All FHIR Elements](explore_birth_details.html#mapping-for-bundle)|    |[View Used FHIR Elements Only](explore_birth_details_used.html#mapping-for-bundle)|

|  **Name** | **Card.** | **Conformance** | **Type** | **Description, Constraints and mapping for DCH Implementation** |
|  :------ | :------ | ------ | :------ | :------ |
|  Bundle | ​ |  |  | Contains a collection of resources<br/>Constraint (bdl-7): FullUrl must be unique in a bundle, or else entries with the same fullUrl must have different meta.versionId<br/>Constraint (bdl-9): A document must have an identifier with a system and a value<br/>Constraint (bdl-3): Entry.Request Only For Some Types Of Bundles<br/>Constraint (bdl-4): Entry.Response Only For Some Types Of Bundles<br/>Constraint (bdl-1): Total Only When A Search Or History<br/>Constraint (bdl-2): Entry.Search Only When A Search |
|  - id | 0..1 | Mandatory | [Id](http://hl7.org/fhir/stu3/datatypes.html#id) | Must contain a UUID to identify the instance of a bundle |
|  - meta | 0..1 | Mandatory | [Meta](http://hl7.org/fhir/stu3/resource.html#Meta) | The profile element MUST contain the value https://fhir.nhs.uk/STU3/StructureDefinition/NHSD-Bundle-1 |
|  - type | 1..1 | Mandatory | [Code](http://hl7.org/fhir/stu3/datatypes.html#code) | document : message : transaction : transaction-response : batch : batch-response : history : searchset : collection<br/>Fixed Value: message<br/>Binding (required): Indicates the purpose of a bundle - how it was intended to be used. (http://hl7.org/fhir/stu3/valueset-bundle-type.html )<br/><span style="color:red">Fixed Value: message</span>. |
|  - entry | 1..* | Mandatory | [BackboneElement](http://hl7.org/fhir/stu3/backboneelement.html) | Entry in the bundle - will have a resource, or information<br/>Constraint (bdl-8): fullUrl cannot be a version specific reference<br/>Constraint (bdl-5): Must Be A Resource Unless There'S A Request Or Response |
|  - - fullUrl | 0..1 | Mandatory | [Uri](http://hl7.org/fhir/stu3/datatypes.html#uri) | Absolute URL for resource (server address, or UUID/OID). This MUST be a UUID prefixed by urn:uuid: |
|  - - resource | 1..1 | Mandatory | [Resource](http://hl7.org/fhir/stu3/resource.html) | A resource in the bundle |




| DCH Data Item                       | FHIR resource element                                                   | Mandatory/Required/Optional |
|-------------------------------------|-------------------------------------------------------------------------|-----------------------------|
| Location of Birth                   | CareConnect-DCH-Delivery-Location-1.identifier (ODS Site Code)           | Required                   |
| Delivery Place Type Code            | CareConnect-DCH-Delivery-Location-1.physicalType                        | Mandatory                   |
| Birth Order                         | CareConnect-DCH-Patient-1.multipleBirthInteger                     | Mandatory                   |
| Length of Gestation at Birth        | CareConnect-DCH-LengthOfGestation-Observation-1.valueQuantity           | Mandatory                   |
| Number of Births in confinement     | CareConnect-DCH-NumberOfBirths-Observation-1.valueQuantity                  | Mandatory                    |
| Problems during Delivery            | CareConnect-DCH-ProblemDuringDelivery-Condition-1.code                          | Required                    |
| Physical Problems detected at Birth | CareConnect-DCH-PhysicalProblemAtBirth-Condition-1.code            | Required                    |
| Neonatal Resuscitation Method       | CareConnect-DCH-NeonatalResuscitationMethod-Procedure-1.code                           | Required                 |
| Date and Time of Birth              | CareConnect-DCH-Patient-1.birthDate (with patient-BirthTime extension)                           | Mandatory                 |
| Type of Delivery                    | CareConnect-DCH-FinalDeliveryType-Procedure-1.code   | Mandatory                    |
| Attempted Type of Delivery          | CareConnect-DCH-AttemptedDeliveryType-Condition-1.code   | Required                    |
| Onset of Spontaneous Respiration    | CareConnect-DCH-SpontaneousRespirationOnset-Observation-1.component  | Optional                    |
| APGAR Score (1 Minute)              | CareConnect-DCH-APGARScore-Observation-1.valueQuantity                 | Mandatory                   |
| APGAR Score (5 Minute)              | CareConnect-DCH-APGARScore-Observation-1.valueQuantity                  | Mandatory                   |
| APGAR Score (10 Minute)             | CareConnect-DCH-APGARScore-Observation-1.valueQuantity                | Optional                    |
| Put To Breast                       | CareConnect-DCH-PutToBreastIndicator-Observation-1.code                  | Required                    |
| Identical Twin Indicator	      | CareConnect-DCH-IdenticalTwinIndicator-Observation-1.code               | Optional                    |

