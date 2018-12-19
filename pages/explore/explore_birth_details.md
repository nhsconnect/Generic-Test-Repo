---
title: Birth Details Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_birth_details.html
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


## Mapping for Bundle ##

|>|Level 1|[Bundle Resource](http://hl7.org/fhir/stu3/bundle.html)|>|Level 2| None|>|Level 3|[NHSD-Bundle-1 Profile](http://xxx)|

|**View All FHIR Elements**|    |**[View Used FHIR Elements Only](explore_birth_details_used.html#mapping-for-bundle)**|

|  **Name** | **Card.** | **Conformance** | **Type** | **Description, Constraints and mapping for DCH Implementation** |
|  :------ | :------ | ------ | :------ | :------ |
|  Bundle | ​ |  |  | Contains a collection of resources<br/>Constraint (bdl-7): FullUrl must be unique in a bundle, or else entries with the same fullUrl must have different meta.versionId<br/>Constraint (bdl-9): A document must have an identifier with a system and a value<br/>Constraint (bdl-3): Entry.Request Only For Some Types Of Bundles<br/>Constraint (bdl-4): Entry.Response Only For Some Types Of Bundles<br/>Constraint (bdl-1): Total Only When A Search Or History<br/>Constraint (bdl-2): Entry.Search Only When A Search |
|  - id | 0..1 | Mandatory | [Id](http://hl7.org/fhir/stu3/datatypes.html#id) | Must contain a UUID to identify the instance of a bundle |
|  - meta | 0..1 | Mandatory | [Meta](http://hl7.org/fhir/stu3/resource.html#Meta) | The profile element MUST contain the value https://fhir.nhs.uk/STU3/StructureDefinition/NHSD-Bundle-1 |
|  - implicitRules | 0..1 | Not Used | [Uri](http://hl7.org/fhir/stu3/datatypes.html#uri) | A set of rules under which this content was created |
|  - language | 0..1 | Not Used | [Code](http://hl7.org/fhir/stu3/datatypes.html#code) | [Language of the resource content . Binding (extensible): A human language. ( http://hl7.org/fhir/stu3/valueset-languages.html )](http://hl7.org/fhir/stu3/valueset-languages.html) |
|  - identifier | 0..1 | Not Used | [Identifier](http://hl7.org/fhir/stu3/datatypes.html#identifier) | Persistent identifier for the bundle |
|  - - use | 0..1 | Not Used | [Code](http://hl7.org/fhir/stu3/datatypes.html#code) | [usual : official : temp : secondary (If known) Binding (required): Identifies the purpose for this identifier, if known . ( http://hl7.org/fhir/stu3/valueset-identifier-use.html )](http://hl7.org/fhir/stu3/valueset-identifier-use.html) |
|  - - type | 0..1 | Not Used | [CodeableConcept](http://hl7.org/fhir/stu3/datatypes.html#codeableconcept) | Description of identifier<br/>Binding (extensible): A coded type for an identifier that can be used to determine which identifier to use for a specific purpose. ( http://hl7.org/fhir/stu3/valueset-identifier-type.html ) |
|  - - system | 1..1 | Not Used | [Uri](http://hl7.org/fhir/stu3/datatypes.html#uri) | The namespace for the identifier value |
|  - - value | 1..1 | Not Used | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | The value that is unique |
|  - - period | 0..1 | Not Used | [Period](http://hl7.org/fhir/stu3/datatypes.html#period) | Time period when id is/was valid for use<br/>Constraint (per-1): If present, start SHALL have a lower value than end |
|  - - assigner | 0..1 | Not Used | [Reference](http://hl7.org/fhir/stu3/references.html) | Organization that issued id (may be just text)<br/>Constraint (ref-1): SHALL have a contained resource if a local reference is provided |
|   |  | Not Used | CareConnect-NHSD-Organization-1 |  |
|  - type | 1..1 | Mandatory | [Code](http://hl7.org/fhir/stu3/datatypes.html#code) | document : message : transaction : transaction-response : batch : batch-response : history : searchset : collection<br/>Binding (required): Indicates the purpose of a bundle - how it was intended to be used. (http://hl7.org/fhir/stu3/valueset-bundle-type.html )<br/>Fixed Value: "message" |
|  - entry | 1..* | Mandatory | [BackboneElement](http://hl7.org/fhir/stu3/backboneelement.html) | Entry in the bundle - will have a resource, or information<br/>Constraint (bdl-8): fullUrl cannot be a version specific reference<br/>Constraint (bdl-5): Must Be A Resource Unless There'S A Request Or Response |
|  - - modifierExtension | 0..* | Not Used | [Extension](http://hl7.org/fhir/stu3/extensibility.html#Extension) | Extensions that cannot be ignored<br/>Constraint (ext-1): Must have either extensions or value[x], not both |
|  - - fullUrl | 0..1 | Mandatory | [Uri](http://hl7.org/fhir/stu3/datatypes.html#uri) | Absolute URL for resource (server address, or UUID/OID). This MUST be a UUID prefixed by urn:uuid: |
|  - - resource | 1..1 | Mandatory | [Resource](http://hl7.org/fhir/stu3/resource.html) | [A resource in the bundle. This MUST be to the message Header resource profiled as NHSD-MessageHeader-1](explore_birth_details_used.html#mapping-for-messageHeader) |

## Mapping for MessageHeader ##

|>|Level 1|[MessageHeader Resource](http://hl7.org/fhir/stu3/messageHeader.html)|>|Level 2| None|>|Level 3|[NHSD-MessageHeader-1 Profile](http://xxx)|

|**View All FHIR Elements**|    |**[View Used FHIR Elements Only](explore_birth_details_used.html#mapping-for-messageheader)**|


|  **Name** | **Card.** | **Conformance** | **Type** | **Description, Constraints and mapping for DCH Implementation** |
|  ------ | :------ | ------ | :------ | :------ |
|  MessageHeader | ​ |  |  | A resource that describes a message that is exchanged between systems<br/>Constraint (dom-2): If the resource is contained in another resource, it SHALL NOT contain nested Resources<br/>Constraint (dom-1): If the resource is contained in another resource, it SHALL NOT contain any narrative<br/>Constraint (dom-4): If a resource is contained in another resource, it SHALL NOT have a meta.versionId or a meta.lastUpdated<br/>Constraint (dom-3): If the resource is contained in another resource, it SHALL be referred to from elsewhere in the resource |
|  - id | 1..1 | Mandatory | [Id](http://hl7.org/fhir/stu3/datatypes.html#id) | Logical id of this artifact. This MUST be a UUID. |
|  - meta | 0..1 | Mandatory | [Meta](http://hl7.org/fhir/stu3/resource.html#Meta) | Metadata about the resource. The profile element MUST contain the value https://fhir.nhs.uk/STU3/StructureDefinition/NHSD-MessageHeader-1 |
|  - implicitRules | 0..1 | Not Used | [Uri](http://hl7.org/fhir/stu3/datatypes.html#uri) | A set of rules under which this content was created |
|  - language | 0..1 | Not Used | [Code](http://hl7.org/fhir/stu3/datatypes.html#code) | [Language of the resource content Binding (extensible): A human language. ( http://hl7.org/fhir/stu3/valueset-languages.html )](http://hl7.org/fhir/stu3/valueset-languages.html) |
|  - text | 0..1 | Not Used | [Narrative](http://hl7.org/fhir/stu3/narrative.html#Narrative) | Text summary of the resource, for human interpretation |
|  - contained | 0..* | Not Used | [Resource](http://hl7.org/fhir/stu3/resource.html) | Contained, inline Resources |
|  - extension (messageEventType) | 1..1 | Mandatory | https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-MessageEventType-1 | [The url attribute of the extension element MUST contain the value https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-MessageEventType-1 and populated as per specified here.](http://birth_details_used.html#extension-MessageUpdateType-1) |
|  - modifierExtension | 0..* | Not Used | [Extension](http://hl7.org/fhir/stu3/extensibility.html#Extension) | Extensions that cannot be ignored<br/>Constraint (ext-1): Must have either extensions or value[x], not both<br/>Slicing: Description: Extensions are always sliced by (at least) url, Discriminator: url, Ordering: false, Rules: Open |
|  - event | 0..* | Mandatory | [Coding](http://hl7.org/fhir/stu3/datatypes.html#coding) | [Code for the event this message represents - Binding (required): The type of Child Health Event.](https://fhir.nhs.uk/STU3/ValueSet/DCH-ChildHealthEventType-1) |
|  - - system | 1..1 | Mandatory | [Uri](http://hl7.org/fhir/stu3/datatypes.html#uri) | Identity of the terminology system. MUST contain the Fixed Value: "https://fhir.nhs.uk/STU3/CodeSystem/DCH-ChildHealthEventType-1" |
|  - - version | 1..1 | Not Used | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | Version of the system - if relevant |
|  - - code | 0..1 | Mandatory | [Code](http://hl7.org/fhir/stu3/datatypes.html#code) | [Symbol in syntax defined by the system. MUST contain a value from the ValueSet ( https://fhir.nhs.uk/STU3/ValueSet/DCH-ChildHealthEventType-1](https://fhir.nhs.uk/STU3/ValueSet/DCH-ChildHealthEventType-1 ) |
|  - - display | 1..1 | Mandatory | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | Representation defined by the system. MUST contain the display text assoicated  with the code carried in the code element |
|  - timestamp | 1..1 | Mandatory | [Instant](http://hl7.org/fhir/stu3/datatypes.html#instant) | Time that the message was sent |
|  - source | 1..1 | Mandatory | [BackboneElement](http://hl7.org/fhir/stu3/backboneelement.html) | Message source application |
|  - - modifierExtension | 1..1 | Not Used | [Extension](http://hl7.org/fhir/stu3/extensibility.html#Extension) | Extensions that cannot be ignored<br/>Constraint (ext-1): Must have either extensions or value[x], not both |
|  - - name | 0..* | Not Used | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | Name of system |
|  - - software | 0..1 | Not Used | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | Name of software running the system |
|  - - version | 0..1 | Not Used | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | Version of software running |
|  - - contact | 0..1 | Not Used | [ContactPoint](http://hl7.org/fhir/stu3/datatypes.html#contactpoint) | Human contact for problems<br/>Constraint (cpt-2): A system is required if a value is provided. |
|  - - - system | 0..1 | Not Used | [Code](http://hl7.org/fhir/stu3/datatypes.html#code) | [phone : fax : email : pager : url : sms : other. Binding (required): Telecommunications form for contact point ( http://hl7.org/fhir/stu3/valueset-contact-point-system.html )](http://hl7.org/fhir/stu3/valueset-contact-point-system.html) |
|  - - - value | 0..1 | Not Used | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | The actual contact point details |
|  - - - use | 0..1 | Not Used | [Code](http://hl7.org/fhir/stu3/datatypes.html#code) | [home : work : temp : old : mobile - purpose of this contact point. Binding (required): Use of contact point ( http://hl7.org/fhir/stu3/valueset-contact-point-use.html )](http://hl7.org/fhir/stu3/valueset-contact-point-use.html) |
|  - - - rank | 0..1 | Not Used | [positiveInt](http://hl7.org/fhir/stu3/datatypes.html#positiveint) | Specify preferred order of use (1 = highest) |
|  - - - period | 0..1 | Not Used | [Period](http://hl7.org/fhir/stu3/datatypes.html#period) | Time period when the contact point was/is in use<br/>Constraint (per-1): If present, start SHALL have a lower value than end |
|  - - - - start | 0..1 | Not Used | [dateTime](http://hl7.org/fhir/stu3/datatypes.html#datetime) | Starting time with inclusive boundary |
|  - - - - end | 0..1 | Not Used | [dateTime](http://hl7.org/fhir/stu3/datatypes.html#datetime) | End time with inclusive boundary, if not ongoing |
|  - - endpoint | 1..1 | Mandatory | [Uri](http://hl7.org/fhir/stu3/datatypes.html#uri) | Actual message source address or id |
|  - responsible | 1..1 | Mandatory | [Reference](http://hl7.org/fhir/stu3/references.html) | Final responsibility for event<br/>Constraint (ref-1): SHALL have a contained resource if a local reference is provided |
|   |  | Mandatory | CareConnect-NHSD-Organization-1 | [The responsible organization carried in the Organizaion resource in the bundle. This MUST be to the Organization resource profiled as CareConnect-NHSD-Organization-1](birth_details_used.html#mapping-for-organization) |
|  - - reference | 1..1 | Mandatory | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | Literal reference, Relative, internal or absolute URL |
|  - - identifier | 0..1 | Not Used | [Identifier](http://hl7.org/fhir/stu3/datatypes.html#identifier) | Logical reference, when literal reference is not known |
|  - - display | 0..1 | Not Used | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | Text alternative for the resource |
|  - focus | 1..1 | Mandatory | [Reference](http://hl7.org/fhir/stu3/references.html) | The actual content of the message<br/>Constraint (ref-1): SHALL have a contained resource if a local reference is provided |
|   |  | Mandatory | CareConnect-NHSD-Encounter-1 | [The focus resource in the bundle. This MUST be to the encounter resource profiled as CareConnect-NHSD-Encounter-1](http://birth_details_used.html#mapping-for-encounter) |
|  - - reference | 1..1 | Mandatory | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | Literal reference, Relative, internal or absolute URL |
|  - - identifier | 0..1 | Not Used | [Identifier](http://hl7.org/fhir/stu3/datatypes.html#identifier) | Logical reference, when literal reference is not known |
|  - - display | 0..1 | Not Used | [String](http://hl7.org/fhir/stu3/datatypes.html#string) | Text alternative for the resource |








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

