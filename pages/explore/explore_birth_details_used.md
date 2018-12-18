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

|>|Level 1|[Bundle Resource](http://hl7.org/fhir/stu3/bundle.html)|>|Level 2| None|>|Level 3|[NHSD-Bundle-1 Profile](http://xxx)|

|[View All FHIR Elements](explore_birth_details.html#mapping-for-bundle)|    |**[View Used FHIR Elements Only](explore_birth_details_used.html#mapping-for-bundle)**|

|  **Name** | **Card.** | **Conformance** | **Type** | **Description, Constraints and mapping for DCH Implementation** |
|  :------ | :------ | ------ | :------ | :------ |
|  Bundle | ​ |  |  | Contains a collection of resources<br/>Constraint (bdl-7): FullUrl must be unique in a bundle, or else entries with the same fullUrl must have different meta.versionId<br/>Constraint (bdl-9): A document must have an identifier with a system and a value<br/>Constraint (bdl-3): Entry.Request Only For Some Types Of Bundles<br/>Constraint (bdl-4): Entry.Response Only For Some Types Of Bundles<br/>Constraint (bdl-1): Total Only When A Search Or History<br/>Constraint (bdl-2): Entry.Search Only When A Search |
|  - id | 0..1 | Mandatory | [Id](http://hl7.org/fhir/stu3/datatypes.html#id) | Must contain a UUID to identify the instance of a bundle |
|  - meta | 0..1 | Mandatory | [Meta](http://hl7.org/fhir/stu3/resource.html#Meta) | The profile element MUST contain the value https://fhir.nhs.uk/STU3/StructureDefinition/NHSD-Bundle-1 |
|  - type | 1..1 | Mandatory | [Code](http://hl7.org/fhir/stu3/datatypes.html#code) | document : message : transaction : transaction-response : batch : batch-response : history : searchset : collection<br/>Binding (required): Indicates the purpose of a bundle - how it was intended to be used. (http://hl7.org/fhir/stu3/valueset-bundle-type.html )<br/>Fixed Value: "message" |
|  - entry | 1..* | Mandatory | [BackboneElement](http://hl7.org/fhir/stu3/backboneelement.html) | Entry in the bundle - will have a resource, or information<br/>Constraint (bdl-8): fullUrl cannot be a version specific reference<br/>Constraint (bdl-5): Must Be A Resource Unless There'S A Request Or Response |
|  - - fullUrl | 0..1 | Mandatory | [Uri](http://hl7.org/fhir/stu3/datatypes.html#uri) | Absolute URL for resource (server address, or UUID/OID). This MUST be a UUID prefixed by urn:uuid: |
|  - - resource | 1..1 | Mandatory | [Resource](http://hl7.org/fhir/stu3/resource.html) | [A resource in the bundle. This MUST be to the message Header resource profiled as NHSD-MessageHeader-1](birth_details_used.html#mapping-for-messageHeader) |

## Mapping for MessageHeader ##

|>|Level 1|[MessageHeader Resource](http://hl7.org/fhir/stu3/messageHeader.html)|>|Level 2| None|>|Level 3|[NHSD-MessageHeader-1 Profile](http://xxx)|

|[View All FHIR Elements](explore_birth_details.html#mapping-for-messageheader)|    |[View Used FHIR Elements Only](explore_birth_details_used.html#mapping-for-messageheader)|

|  **Name** | **Card.** | **Conformance** | **Type** | **Description, Constraints and mapping for XXX Implementation** |
|  :------ | :------ | ------ | :------ | :------ |
|  MessageHeader | ​ |  |  | A resource that describes a message that is exchanged between systems<br/>Constraint (dom-2): If the resource is contained in another resource, it SHALL NOT contain nested Resources<br/>Constraint (dom-1): If the resource is contained in another resource, it SHALL NOT contain any narrative<br/>Constraint (dom-4): If a resource is contained in another resource, it SHALL NOT have a meta.versionId or a meta.lastUpdated<br/>Constraint (dom-3): If the resource is contained in another resource, it SHALL be referred to from elsewhere in the resource |
|  id | 1..1 | Mandatory | Id | Logical id of this artifact |
|  meta | 0..1 | Mandatory | Meta | Metadata about the resource |
|  extension (messageEventType) | 1..1 | Mandatory | Extension | The type of event applicable to the Child Health event message<br/>Constraint (ext-1): Must have either extensions or value[x], not both<br/>URL: https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-MessageEventType-1 |
|  event | 1..1 | Mandatory | Coding | Code for the event this message represents<br/>Binding (required): The type of Child Health Event ( https://fhir.nhs.uk/STU3/ValueSet/DCH-ChildHealthEventType-1 ) |
|  system | 1..1 | Mandatory | Uri | Identity of the terminology system<br/>Fixed Value: https://fhir.nhs.uk/STU3/CodeSystem/DCH-ChildHealthEventType-1 |
|  code | 1..1 | Mandatory | Code | Symbol in syntax defined by the system |
|  display | 1..1 | Mandatory | String | Representation defined by the system |
|  timestamp | 1..1 | Mandatory | Instant | Time that the message was sent |
|  source | 1..1 | Mandatory | BackboneElement | Message source application |
|  modifierExtension | 0..* | Mandatory | Extension | Extensions that cannot be ignored<br/>Constraint (ext-1): Must have either extensions or value[x], not both |
|  name | 0..1 | Mandatory | String | Name of system |
|  software | 0..1 | Mandatory | String | Name of software running the system |
|  version | 0..1 | Mandatory | String | Version of software running |
|  contact | 0..1 | Mandatory | ContactPoint | Human contact for problems<br/>Constraint (cpt-2): A system is required if a value is provided. |
|  system | 0..1 | Mandatory | Code | phone <code>&amp;#124;</code> fax <code>&amp;#124;</code> email <code>&amp;#124;</code> pager <code>&amp;#124;</code> url <code>&amp;#124;</code> sms <code>&amp;#124;</code> other<br/>Binding (required): Telecommunications form for contact point ( http://hl7.org/fhir/stu3/valueset-contact-point-system.html ) |
|  value | 0..1 | Mandatory | String | The actual contact point details |
|  use | 0..1 | Mandatory | Code | home <code>&amp;#124;</code> work <code>&amp;#124;</code> temp <code>&amp;#124;</code> old <code>&amp;#124;</code> mobile - purpose of this contact point<br/>Binding (required): Use of contact point ( http://hl7.org/fhir/stu3/valueset-contact-point-use.html ) |
|  rank | 0..1 | Mandatory | positiveInt | Specify preferred order of use (1 = highest) |
|  period | 0..1 | Mandatory | Period | Time period when the contact point was/is in use<br/>Constraint (per-1): If present, start SHALL have a lower value than end |
|  start | 0..1 | Mandatory | dateTime | Starting time with inclusive boundary |
|  end | 0..1 | Mandatory | dateTime | End time with inclusive boundary, if not ongoing |
|  endpoint | 1..1 | Mandatory | Uri | Actual message source address or id |
|  responsible | 1..1 | Mandatory | Reference ( Practitioner <code>&amp;#124;</code>Organization ) | Final responsibility for event<br/>Constraint (ref-1): SHALL have a contained resource if a local reference is provided |
|  reference | 1..1 | Mandatory | String | Literal reference, Relative, internal or absolute URL |
|  identifier | 0..1 | Optional | Identifier | Logical reference, when literal reference is not known |
|  display | 0..1 | Optional | String | Text alternative for the resource |
|  focus | 1..1 | Mandatory | Reference ( CareConnect-DCH-Encounter-1 <code>&amp;#124;</code>CareConnect-DCH-Emergency-Encounter-1 ) | The actual content of the message<br/>Constraint (ref-1): SHALL have a contained resource if a local reference is provided |
|  reference | 1..1 | Mandatory | String | Literal reference, Relative, internal or absolute URL |
|  identifier | 0..1 | Mandatory | Identifier | Logical reference, when literal reference is not known |
|  display | 0..1 | Mandatory | String | Text alternative for the resource | 




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

