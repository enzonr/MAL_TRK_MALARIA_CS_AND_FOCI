# Malaria Elimination Case Surveillance &amp; Foci Investigation System Design

## Introduction

Transforming the surveillance system into a core intervention is the third pillar of the [_Global technical strategy for malaria 2016–2030_](https://www.who.int/publications-detail-redirect/9789240031357)_._ As countries progress towards malaria elimination, the aim of surveillance is to detect all malaria cases; investigate every confirmed malaria case; identify the likely location of an infection in order to direct actions to interrupt transmission and to ensure that each detected case is promptly treated and monitored to prevent secondary infection. An ideal surveillance information system for malaria elimination includes rapid and complete case reporting, central data storage and management, automated data analysis, and customized outputs and feedback that lead to timely and targeted responses. The DHIS2 tracker package for malaria case surveillance and foci investigation is an aid for malaria surveillance in burden reduction and elimination settings.

The data elements included follow WHO-recommendations based on WHO global standards and normative guidance as stipulated in the organisations guidelines and guiding documents; in particular, the [Malaria Surveillance, Monitoring and Evaluation Manual]([https://apps.who.int/iris/bitstream/handle/10665/272284/9789241565578-eng.pdf](https://apps.who.int/iris/bitstream/handle/10665/272284/9789241565578-eng.pdf)). The data gathered is rendered into actionable indicators and dashboards in line with the work of the WHO surveillance assessment toolkit. The tracker packages supporting case notification, case investigation, foci investigation and classification workflows are designed to be used in conjunction with the aggregate DHIS2 packages for malaria programme monitoring in elimination and burden reduction settings to strengthen data quality, analysis and data driven decision making.

## System design overview

The metadata package contains two tracker programs that support the notification, investigation and classification of malaria cases and malaria foci as part of national malaria surveillance strategies. hese tracker programs are intended to be packaged and deployed together to serve complementary, related workflows for case notification and case and foci investigation systems.  The figure below illustrates elimination surveillance with the examples of case notification within 1 day, case investigation within 3 days and focus investigation within 7 days, a “1–3–7” approach adopted from the guidance in China.




**MAL CS - Malaria Case Notification, Investigation &amp; Response:** This is a longitudinal case-based surveillance program that supports a typical workflow for notifying confirmed malaria cases and following them up through case investigation  and case classification and focus investigation. 


It allows for cases to be linked through relationships- case to cases (detected reactively) and; a case to a foci registered in the related tracker program &quot;Foci Investigation&quot;. The &quot;Foci Investigation&quot; programme provides details on the actions taken around the index case that triggered a case investigation and the appropriate response measures that were carried out within the focus.

**MAL Malaria Foci Investigation Program (MAL-FOCI)** is a registry of all foci and their classification status, as well as response interventions taken to manage them and potential for reclassification should the need arise._


 There are also seven dashboards which are populated with indicators from the respective programs. The programmes are made to work in tandem and fulfill different aspects of the malaria elimination and burden reduction process._

## Program structure

### 2.2.1 Program summary

 MAL-CS:

| Stage | Description |
|---|---|
| Enrollment | This section identifies information about the case and its surroundings. When a patient is enrolled in the case- based programme, they are also enrolled into their current organisation unit and assigned a unique ID. This enrollment also serves as a case notification which is necessary to trigger an investigation. |
| Diagnosis and treatment stage | This stage records information about the diagnosis of the patient, how they were detected, if they had any previous malaria diagnosis and travel history of the patient which is necessary for a case to be preliminarily classified. This stage would ideally happen at the health facility level and  completed typically within 24 hours (1 day) of detection. |
| Case investigation and classification | In this stage, the index case will further be investigated at the household level.This involves the screening for malaria of all household members, capturing of the household coordinated and recording of  any vector control interventions undertaken. All newly diagnosed  malaria cases detected  while screening members of the household will be recorded and a separate case notification form will be filled out. This stage is to be completed typically within 3 days of detection. |
| Neighbouring household investigation | This stage allows the investigators to investigate neighbouring households which are located within a predetermined radius around the index case. This stage involves the screening for malaria of all household members,  capturing the neighbouring households' coordinates and recording  of any vector control interventions that were carried out. Once again, all newly diagnosed malaria cases detected while screening household members will be recorded and  a separate case notification form will be filled out. This is a repeatable stage and for each household visited a new neighbouring  household investigation will be filled out. This stage is to be completed ideally within 3 days of index case detection. |
| Case outcome | In this stage once all investigations are concluded, registration of  the final case classification as well as the outcome of the patient is recorded. This stage is to be completed ideally within 3 days of detection. |
| Routine focus investigation | This stage allows for a regular investigation around the predetermined area where the index case is located. The routine focus investigation is conducted. Ideally within 7 days of every passively detected case. |

MAL-FOCI

| Stage | Description |
| --- | --- |
| Enrollment | This stage gathers basic information about the foci ranging from the date of its registration to the foci name and is assigned with a unique ID, creating a foci profile. |
| Focus status, investigation and classification | This is a repeatable stage where the status of the focus is recorded and the focus is classified. It further records more detailed information about the focus as well as entomological activities and findings.. |
| Foci Response | This stage records vector control interventions carried out in this focus. |

### 2.2.2. Workflow

![Shape1](RackMultipart20211119-4-1qe0v2k_html_ab632a35e807e97.gif)

The program assumes that all people registered have tested positive for malaria and is divided in five non-repeatable stages which follow the case through the lifetime of their enrollment.

## 2.3.Intended users

_The programme is intended to be used at point of care facilities for data entry purposes, and the indicators populate dashboards that are thought to be used at national, district, facility levels. Currently, data-entry users have access to all the stages, but depending on in-country workflows they could be divided by program stage, for example, granting only the investigation team access to the investigation stage._

2.4 User Groups

 User groups have been divided based on the program that they will be assigned to use and the function that the user is intended to perform. A user can belong to more than one user group if their functions overlap. In addition, further compartmentalisation can be made through assigning specific user groups for the different stages. Users will also need to be assigned an organisation unit.

_MAL-CS_

 **MAL-CS- Data Analysis**: Has access to all dashboards but cannot modify metadata or enter new data

 **MAL-CS- Data Entry**: Can enter data and create new patient records

 **MAL-CS- Metadata Admin**: Can modify the metadata

_The implementing country should ensure that users have data entry and search rights for their respective Organisation units._

_MAL-FOCI_

**MAL-FOCI- Data Analysis**: Has access to all dashboards but cannot modify metadata or enter new data

**MAL-FOCI- Data Entry**: Can enter data and create new patient records_

**MAL-FOCI- Metadata Admin**: Can modify the metadata

## 3. Tracker Configuration

## 3.1 Program configuration

### 3.1.1 MAL-CS Program configuration

The &quot;Malaria case notification, investigation and response&quot; program follows a confirmed malaria case throughout their treatment from when they are diagnosed with malaria. A patient can be enrolled as a case on the programme on more than one occasion. The case is represented by the tracked entity type "Malaria Case"

 The program displays the front page list in order to have an at a glance list of cases in the organisation unit, and it requires a minimum of two attributes to search for cases with 50 maximum of TEIs to return in search.

 The program has been set as &quot;Audited&quot; meaning that users have access to enrollments in other org units, but that an audit trail of who has accessed which records is kept. For a more secure approach where access is more restricted, see here: [https://docs.dhis2.org/en/develop/using-the-api/dhis-core-version-236/new-tracker.html#webapi\_nti\_access\_level](https://docs.dhis2.org/en/develop/using-the-api/dhis-core-version-236/new-tracker.html#webapi_nti_access_level)

### 3.1.2 MAL-FOCI Program configuration

The Malaria Foci Investigation program registers all the foci which have been identified. A foci is defined by the WHO as &quot;a defined and circumscribed zone situated in an area that is or has been malarious and in which the necessary epidemiological and ecological factors are present for the transmission of malaria&quot;. The foci are represented by the tracked entity type "focus area"

 The program displays the front page list in order to have an at a glance list of foci in the org unit, and it requires a minimum of one attribute to search for foci with no maximum of TEIs to return in search.

 As foci are not people, they do not have sensitive personal information registered in their enrollment, they have been set with access level &quot;open&quot;. This should be evaluated by local data protection legislation.

 It currently has no feature point to capture coordinates at enrollment level as these are captured in the investigation stage.

## 3.2 prefixes

Throughout the metadata package, elements are prefixed with either "MAL" an object which os shared with other Malaria programmes, "MAL-CS" an object which is for the case surveillance program, &quot;MAL-FOCI&quot; for objects which are part of the Malaria Foci programme, and GEN, which are generic for our standard metadata packages.

## 3.3 Unique Identifiers

The programs use different unique identifiers to aid with deduplication and with locating a case/foci. These include automatically generated IDs and should be adapted to local needs.

 System Case ID - An identifier which is unique for the whole system with an automatically generated pattern in the format RANDOM(XXX######).

 Malaria Local Case - ID An identifier which is unique for the whole system. It is currently not automatically generated to allow for it to be based on for example, a paper record.

 Focus ID - An identifier which is unique for the whole system with an automatically generated pattern in the format RANDOM(XXX##)

 For more information about the text patterns in DHIS2, see here [https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/additional-information/dhis2-tutorials.html#working-with-textpattern](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/additional-information/dhis2-tutorials.html#working-with-textpattern)

## 3.4Tracked Entity type

MAL-CS:

The Case Surveillance program uses the tracked entity type &quot;Case&quot; instead of &quot;Person&quot; which is what is commonly used in our metadata packages. This means that each time someone becomes infected, they become a case. A case is only allowed to be enrolled once. If someone becomes re-infected with malaria, they will have to be registered as a new case, and there are fields (in the diagnosis and treatment stage) where information about their previous infection can be recorded.

 This means that there could be several &quot;case&quot; tracked entities which represent the same individual, and have the same National ID number, and therefore, this attribute should not be unique for the instance. A new &quot;System case ID&quot; is generated for each case.

 Depending on implementation needs, an alternative would be to use the tracked entity type &quot;person&quot; and allow for multiple enrollments. In such case, it would require a new case ID for every time an infection is recorded, which results in a new enrollment, and therefore it should not be an attribute in the enrollment of the person and should rather be added as a data element in a program stage.

 MAL-FOCI:

 The Foci program uses the tracked entity type &quot;Focus Area&quot;, with the mandatory attributes &quot;Focus ID&quot; and &quot;Focus Name&quot;

## 3.4 Relationships

The package includes two bidirectional relationship types, case to foci and case to case, using the [relationships widget](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-235/tracking-individual-level-data/tracker-capture.html#add_relationship_to_tracked_entity_instance).

 Case to foci allows the user to connect a case with an existing or new foci. Likewise, it allows for a foci to connect with a case. The foci are registered into the separate &quot;Foci Investigation&quot; programme. See installation guide for more information.

 Case to case connects two malaria cases to each other, and potentially, to other cases.

 ![](RackMultipart20211119-4-1qe0v2k_html_cdb09891e93f9273.png)

The information shown in the relationship widget can be changed by adding the attributes to the tracked entity type and marking the box &quot;show in list&quot;.

## 4.Stages in Detail

## 4.1 MAL-CS

### 4.1.1 Enrollment

In the enrollment stage, each case is registered and assigned a System case ID as well as a Malaria case ID. These can be configured to be automatically generated and unique, depending on the needs of the implementation.

| Name | UID | Value type | Options/Logic (if applicable) | Mandatory? |
| --- | --- | --- | --- | --- |
| Enrollment date | qDkgAbB5Jlk | DATE |
 | YES |
| System Case ID | HAZ7VQ730yn | TEXT | Automatically assigned | NO |
| Malaria Local Case ID | NXazwhBRpfA | TEXT |
 | NO |
| First Name | sB1IHYu2xQT | TEXT |
 | NO |
| Surname | ENRjVGxVL6l | TEXT |
 | NO |
| Date of birth | NI0QRzJvQ0k | DATE |
 | NO |
| Date of birth is estimated | Z1rLc1rVHK8 | TRUE\_ONLY |
 | NO |
| Age (years) | B6TnnFMgmCk | INTEGER\_ZERO\_OR\_POSITIVE | Calculated by program rule | NO |
| Sex | oindugucx72 | TEXT | FEMALEMALE | NO |
| Pregnancy Status | sPDKWSQ2vKQ | TEXT |
 Only visible if Female of reproductive age /
 YESNO | NO |
| Malaria - Occupation | ZZmkcCkzzWr | TEXT | NURSE STUDENT TEACHER TRUCKDRIVER MINEWORKER SEASONALWORKER MIGRANTWORKER FARMER | NO |
| Present Home Address | CpDhdm55uhl | TEXT |
 | NO |
| Address (permanent) | XN0145qZ7kH | TEXT |
 | NO |
| Nationality | spkM2E9dn2J | TEXT | Complete country list ISO codes | NO |
| Mobile phone number | fctSQp5nAYl | PHONE\_NUMBER |
 | NO |
| Head of Household (First Name) | YCKldfKePsC | TEXT |
 | NO |
| Head of Household (Last Name) | uLvB95ZxIUL | TEXT |
 | NO |

### 4.1.2 Diagnosis and treatment stage

_This stage is divided into three sections. It is mandatory to enter a date of diagnosis and a case detection setting. Both this elements are heavily used for indicator calculations_

| Section | Name | UID | Value type | Logic/ Options (if any) | Mandatory? |
|---|---|---|---|---|---|
| N/A | Date of diagnosis | hYyB7FUS5eR | DATE |  | YES |
| Case Detection | Detection setting | fazCI2ygYkq | TEXT | PASSIVE REACTIVE PROACTIVE | YES |

_In the Malaria diagnosis section, all data relevant to the diagnosis process are recorded. There are programme rules included to facilitate data entry and hiding options when not relevant._

| Section | Name | UID | Value type | Logic/ Options (if any) | Mandatory? |
|---|---|---|---|---|---|
| Malaria diagnosis | Reason for conducting case investigation | zFiMMpGyBgr | TEXT | Only available if “Proactive is selected in detection setting. DEVELOPMENT_OF_ACTIVITIES POPULATION_MOVEMENT REFUGEE_CRISIS CLIMATIC_TRIGGERS OTHER | NO |
| Malaria diagnosis | Conducting case investigation (other) | J4fIuC5ZLsU | TEXT |  | NO |
| Malaria diagnosis | Temperature | J7hdx5FCJvG | NUMBER |  | NO |
| Malaria diagnosis | Weight | JINgGHgqzSN | INTEGER_POSITIVE |  | NO |
| Malaria diagnosis | Symptom onset date | YEpmDm1I01R | DATE | Calculated by program rule if days with symptoms are added | NO |
| Malaria diagnosis | Symptom onset date is estimated | S6uZEpdNh8o | YES_ONLY |  | NO |
| Malaria diagnosis | Number of days with symptoms | kJiPLxGq2yI | INTEGER_ZERO_OR_POSITIVE | Calculated by program rule if date is added | NO |
| Malaria diagnosis | Malaria Diagnosis confirmed by | qdjVZojEK8S | TEXT | RDT MICROSCOPY OTHER | NO |
| Malaria diagnosis | Diagnosis method (Other) | FxYWTORW4mT | TEXT | Only visible i “Other” is selected | NO |
| Malaria diagnosis | Malaria plasmodium species identified | vGxpKVMkmaW | TEXT | Only visible if a diagnosis method is selectedPF PK PM PO PV MIX OTHER | NO |
| Malaria diagnosis | Malaria positive species (other) | voV7EhjhyJ3 | TEXT |  | NO |
| Malaria diagnosis | Malaria parasite density | Wwu7UAt7bZW | INTEGER_ZERO_OR_POSITIVE | Only visible if “Microscopy” is selected | NO |
| Malaria diagnosis | presence of gametocytes | LCxi1dciA1C | BOOLEAN | Only visible if “Microscopy” is selected | NO |
| Malaria diagnosis | MAL-CS Severity of disease | SzVk2KvkSSd | TEXT | SIMPLE SEVERE | NO |
| Malaria diagnosis | Malaria Medication | nTMP8Aj1rYA | TEXT | AL ALPLUSPQ AS-SP ASPLUSAQ ASPLUSMQ ASPLUSMQPLUSPQ ASPLUSSP ASPLUSSPPLUSPQ CHLOROQUINE DHA-PPQ DHA-PPQPLUSPQ RADICAL_CURE OTHER | NO |
| Malaria diagnosis | Admission Status | MKMyvXshCdB | TEXT | ADMITTED REFERRED OPD | NO |
| Malaria diagnosis | Reason for referral | Zlro25GTcNK | TEXT | Only visible if case admission status is “Referred”FURTHER_MANAGEMENT OUTOFSTOCK | NO |

_The malaria History section deals with data related to previous Malaria infections, including the previous treatment and species identified._

| Section | Name | UID | Value type | Logic/ Options (if any) | Mandatory? |
|---|---|---|---|---|---|
| History of Malaria | Blood transfusion within past 3 months | yO0ZIegEsDk | BOOLEAN |  | NO |
| History of Malaria | history | cpXwLgQTLeO | BOOLEAN |  | NO |
| History of Malaria | Date of previous diagnosis | Urz28endlF6 | DATE | Only available if there is a history of confirmed malaria | NO |
| History of Malaria | plasmodium species (previous) | xTeHON9Jisk | TEXT | Only available if there is a history of confirmed malariaPF PK PM PO PV MIX OTHER | NO |
| History of Malaria | Malaria Medication (previous) | JndDE3YbCEB | TEXT | Only available if there is a history of confirmed malariaAL ALPLUSPQ AS-SP ASPLUSAQ ASPLUSMQ ASPLUSMQPLUSPQ ASPLUSSP ASPLUSSPPLUSPQ CHLOROQUINE DHA-PPQ DHA-PPQPLUSPQ RADICAL_CURE OTHER | NO |

The final section is not visible in the data entry screen, but it is of utmost importance for indicator calculations. It is always hidden through a program rule with the expression &quot;true&quot; meaning it&#39;s always hidden. Both data elements are automatically populated. The Notification date comes from the current date when the report is being filled. And the diagnosis date comes from the &quot;date of diagnosis&quot; feature in the event. The latter one is there to allow for that value to be used in indicators in other stages.

| Section | Name | UID | Value type | Options (if any) | Mandatory? |
|---|---|---|---|---|---|
| Hidden section for indicator purposes (Diagnosis) | Notification date | fPbtS7glDT2 | DATE |  | NO |
| Hidden section for indicator purposes (Diagnosis) | Diagnosis date | ObiXORrILyV | DATE |  | NO |

### 4.1.3 Case investigation and classification

_This is where the magic happens. The case notification, investigation and response is the stage that is recorded as close as possible to the cases. If it is not done at a facility or telephonically, the investigation will most likely be conducted in a mobile device. It includes a feature point where investigators can record the coordinates of the case. These coordinates are then used to populate the geographical dashboards._

 The first section deals with the location of the case_

| Section | Name | UID | Value type | Options (if any) | Mandatory? |
| --- | --- | --- | --- | --- | --- |
| Feature | Event point |
 | Coordinates |
 | NO |
| Feature | Date of case investigation | wYTF0YCHMWr | DATE |
 | YES |
| Case household investigation | Location where case investigation is conducted | xS8sL2MMpc0 | TEXT | HEALTHFACILITYHOUSEHOLDTELEPHONIC | NO |
| Case household investigation | Village name | Th6dW4kwZji | TEXT | Only available if investigation was held in a household | NO |

The travel details section refers to recent travel by the case, both within and outside the country. Basic decision support programme rules are included.

| Section | Name | UID | Value type | Options (if any) | Mandatory? |
|---|---|---|---|---|---|
| Travel Details | Recent travel within the country | hiymQVgVG2v | TEXT | YES NO | NO |
| Travel Details | Travel within country (30 days symptoms) | qpp5fp1RVaX | TEXT | Only available if case has traveled recently YES NO | NO |
| Travel Details | Travel inside country Region/District | SI1D9IfXiI4 | TEXT | Only available if case has traveled recently | NO |
| Travel Details | Travel inside country town/village name | eYOHoeSizJk | TEXT | Only available if case has traveled recently | NO |
| Travel Details | Travel inside country last night | BRNQ61bbt28 | DATE | Only available if case has traveled recently | NO |
| Travel Details | Travel inside country First Night | Oc9Y7jvdU2g | DATE | Only available if case has traveled recently | NO |
| Travel Details | Travel outside country | OhU3RfPlQGR | TEXT | YES NO | NO |
| Travel Details | Travel outside country last month | B1zbtdPXMRk | TEXT | Only available if case has traveled recentlyYES NO | NO |
| Travel Details | Country traveled to | f9xYwUwrHq9 | TEXT | Only available if case has traveled recentlyFull country list | NO |
| Travel Details | Travel outside country Region/District | kwv9fXr7gbj | TEXT | Only available if case has traveled recently | NO |
| Travel Details | Travel outside country town/village name | JZw2d0yzmHB | TEXT | Only available if case has traveled recently | NO |
| Travel Details | Travel outside country last night | mw2Rso4RHEF | DATE | Only available if case has traveled recently | NO |
| Travel Details | Travel outside country first night | JBBAwCahDQ3 | DATE | Only available if case has traveled recently | NO |
| Travel Details | Travel history narrative | i7JwJXVEl2C | TEXT |  | NO |
| Travel Details | Preliminary case classification | bcGuRgKDZei | TEXT | LOCAL IMPORTED INTRODUCED RECRUDESCENT INDUCED | NO |
| Travel Details | Classification Narrative | pIcW9I0z5LL | TEXT |  | NO |

The index case household investigation implies the investigation of the physical location and inhabitants of the case&#39;s dwelling. Basic validation rules are triggered if numbers are not correct (for example, more household members own a net than there are household members)

| Index case household investigation and response | Name of head of household | SlqoeFUJvUV | TEXT |  | NO |
|---|---|---|---|---|---|
| Index case household investigation and response | Number of household members | lezQpdvvGjY | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Index case household investigation and response | Household members tested for malaria | y57kkdyw35d | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Index case household investigation and response | Household members malaria positive | qxWAgIAfZAh | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Index case household investigation and response | Sleeping places | QtZBHQORAvK | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Index case household investigation and response | Household members own net | uPNwmZl8Clb | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Index case household investigation and response | Residents in household who slept under a net the previous night | KA6RY4BB41F | INTEGER |  | YES |
| Index case household investigation and response | Household sprayed in the past 12 months | AeVEKN0zwJJ | BOOLEAN |  | YES |
| Index case household investigation and response | Malaria Vector Control Intervention - Indoor Residual Spraying | oYbOVrpDnRo | YES_ONLY |  | NO |
| Index case household investigation and response | Malaria Vector Control Intervention - LLIN Distribution | CSYSRYrevdf | YES_ONLY |  | NO |
| Index case household investigation and response | Vector Control Intervention - Larval Source Management | wwIvEJUmxx8 | YES_ONLY |  | NO |

_The final section is not visible in the data entry screen, but it is of utmost importance for indicator calculations. It is always hidden through a program rule and both data elements are automatically populated. The two different data elements are automatically filled with data from the diagnosis stage using programme rules._

| Section | Name | UID | Value type | Options (if any) | Mandatory? |
|---|---|---|---|---|---|
| Hidden section for indicator purposes (Investigation) | Detection setting | fazCI2ygYkq | TEXT | PASSIVE REACTIVE PROACTIVE | NO |
| Hidden section for indicator purposes (Investigation) | Diagnosis date | ObiXORrILyV | DATE |  | NO |

### 4.1.4 Neighbouring household investigation

_This stage records the data for the investigations done in the households in the vicinity of the case. Basic validation rules are triggered if numbers are not correct (for example, more household members own a net than there are household members)_

| Section | Name | UID | Value type | Options (if any) | Mandatory? |
|---|---|---|---|---|---|
| Nearby household investigation | Investigation date | VgsOuy9mXyZ | DATE |  | YES |
| Nearby household investigation | Name of head of household | SlqoeFUJvUV | TEXT |  | NO |
| Nearby household investigation | Number of household members | lezQpdvvGjY | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Nearby household investigation | Household members tested for malaria | y57kkdyw35d | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Nearby household investigation | Household members malaria positive | qxWAgIAfZAh | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Nearby household investigation | Sleeping places | QtZBHQORAvK | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Nearby household investigation | Household members own net | uPNwmZl8Clb | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Nearby household investigation | Residents in household who slept under a net the previous night | KA6RY4BB41F | INTEGER |  | NO |
| Nearby household investigation | Household sprayed in the past 12 months | AeVEKN0zwJJ | BOOLEAN |  | NO |
| Nearby household investigation | Malaria Vector Control Intervention - LLIN Distribution | CSYSRYrevdf | yes_ONLY |  | NO |
| Nearby household investigation | Malaria Vector Control Intervention - Indoor Residual Spraying | oYbOVrpDnRo | yes_ONLY |  | NO |

### 4.1.5 Case outcome

_The case outcome records the end of the final case classification and the outcome of the illness with the following data elements:_

| Case outcome | Report date | eHvTba5ijAh | DATE |  | TRUE |
|---|---|---|---|---|:---:|
| Case outcome | Malaria Final case classification | y3CG06h1Clh | TEXT | INDIGENOUS IMPORTED INTRODUCED RECRUDESCENT INDUCED | FALSE |
| Case outcome | Outcome of illness | zXNfOKXRBA9 | TEXT | CURED DIED ABSCONDED | TRUE |

It also includes a hidden section with the data element &quot;Admission status&quot;, which is assigned automatically from the same data element present in the &quot;Diagnostic and Treatment&quot; Stage.

| Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Hidden Section for indicator purposes (Outcome) | Admission Status | MKMyvXshCdB | TEXT | ADMITTED REFERRED OPD | NO |

### 4.1.6 Routine focus investigation and response

This stage is completed following every case outcome. it has five sections and is non repeatable.
In the locality section the user selects if the locality was urban or rural.

| Section | Name | UID | Value type | Options (if any) | Mandatory? |
|---|---|---|---|---|---|
| feature | Date of focus investigation | KwrBvn1EJT3 | DATE |  | YES |
| Locality | Locality | r4GBctr3Xdh | TEXT | URBAN RURAL | NO |

In the Types of population section, users select the type or types of population that exist in the case&#39;s foci. More than one can be selected

| Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Type(s) of populations | MAL- Migrant | BK2d3ktuJWa | YES_ONLY |  | NO |
| Type(s) of populations | MAL- Refugee | HUzRTYRFcYn | YES_ONLY |  | NO |
| Type(s) of populations | MAL- Resident | Cd5AUkJT1mE | YES_ONLY |  | NO |
| Type(s) of populations | MAL- Temporary worker | VJ7qLlRgm7e | YES_ONLY |  | NO |

The response section gathers the date of response.

| Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Response | Date of response | G7f2D1vl3fD | DATE |  | NO |

And finally, the vector control intervention section records intervations undertaken in this focus. Next time there is ain investigation, these interventions will appear in that section.

| Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Vector control interventions | MAL- Follow-up Vector Control Intervention - LLIN Distribution | JhpYDsTUfi2 | YES_ONLY |  | NO |
| Vector control interventions | Bednet distributed | f623C5LloqV | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Vector control interventions | MAL- Follow-up Vector Control Intervention - Indoor Residual Spraying | yhX7ljWZV9q | YES_ONLY |  | NO |
| Vector control interventions | Household sprayed | veWOag0p9n2 | INTEGER_ZERO_OR_POSITIVE |  | NO |
| Vector control interventions | Environmental | UbeFiBkPcUo | YES_ONLY |  | NO |
| Vector control interventions | Follow-up vector control details | zgnTlAH4ZOk | TEXT |  | NO |
| Vector control interventions | Follow-up vector control details | zgnTlAH4ZOk | TEXT |  | NO |

## 4.2 MAL-FOCI

### 4.2.1 Enrollment

In the foci enrollment there are only four attributes in addition to the date of registration.

|| Name | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|
| Date of Foci Registration | M3xtLkYBlKI | DATE |  | YES |
| Malaria foci investigation Focus Name | Kv4fmHVAzwX | TEXT |  | NO |
| Malaria foci investigation Locality | phxAY4PQdsT | TEXT | URBAN RURAL | NO |
| Malaria foci investigation Focus ID | K9innmM1nuW | TEXT |  | NO |
| Malaria foci investigation Focus Definition | cnXnFAStrrd | TEXT | VILLAGEFOCUS DISTRICTFOCUS REGIONFOCUS | NO |

### 4.2.2 Focus Status investigation and classification stage

This is a repeatable stage where the details of the focus investigation are recorded. It has five sections and following the investigation the focus should be classified Subsequent stages will include previous classification and any interventions that might have been undertaken.

The first section is hidden through programme rules if there have not been any interventions or investigations previously. If there have, then the section is displayed and most of these data elements are automatically completed based on the values from their other stages.

 It has a point feature which allows you to record coordinates as a point on the map to mark the location of the focus. The point could alternatively be configured as a "polygon", which would allow you to draw a shape on the map in order to delimit a perimeter for the focus.

| Stage | Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|  | Feature | Point |  | Coordinates |  |  |
|  | Feature | Date of foci investigation | CWaAcQYKVpq | DATE |  | YES |
|  | Focus Status | - Date of classification | Ah29MGrnVjJ | DATE |  | NO |
|  | Focus Status | - Classification | V1OnhZYfSa2 | TEXT | ACTIVE RESIDUAL_NON-ACTIVE CLEARED | NO |
|  | Focus Status | - Previous Vector Control Interventions - LLIN distribution | jhoCqSTA2QB | YES_ONLY |  | NO |
|  | Focus Status | - Previous Vector Control Intervention - INDOOR residual spraying | e6hRE1N1Fcc | YES_ONLY |  | NO |
|  | Focus Status | - Previous Vector Control Intervention - Larval Source management | dbMsAGvictz | YES_ONLY |  | NO |

The Foci investigation section is where the bulk of the work happens.

| Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Foci Investigation | - Total Population in the Focus | HDRons6AfbL | INTEGER_POSITIVE |  | NO |  |
| Foci Investigation | - Malaria Households | VNM6zoPECqd | INTEGER_POSITIVE |  | NO | YES |
| Foci Investigation | MAL- Resident | Cd5AUkJT1mE | YES_ONLY |  | NO | NO |
| Foci Investigation | MAL- Migrant | BK2d3ktuJWa | YES_ONLY |  | NO | NO |
| Foci Investigation | MAL- Temporary worker | VJ7qLlRgm7e | YES_ONLY |  | NO | NO |
| Foci Investigation | MAL- Refugee | HUzRTYRFcYn | YES_ONLY |  | NO | NO |
| Foci Investigation | - Type of Population - Other | QZZA5IfHAAU | YES_ONLY |  | NO | NO |
| Foci Investigation | - Type of Population - Specify Other | ehBd9cR5bq4 | TEXT | Only shown if other is selected | NO |  |
| Foci Investigation | - Geographical features | SaHE38QFFwZ | TEXT | HILLY PLATUE HILLY_AND_PLATUE | NO |  |
| Foci Investigation | - Development activity present | Tj642rK34Qf | YES_ONLY |  | NO |  |
| Foci Investigation | - Development activity type | jzksn7lA2ac | TEXT | Only shown if yes is selected previously--AGRICULTURE CONSTRUCTION MINING PLANTATION OTHER | NO |  |
| Foci Investigation | - Development activity other specify | gd8U1R3ALDA | TEXT | Only shown if other is selected | NO |  |

The vector behaviour section deals with the resting and biting behaviour of the mosquitoes in the area.

| Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Vector Behaviour | - Biting Behaviour | PxKiOhLn7mV | TEXT | INDOORBITING OUTDOORBITING | NO |
| Vector Behaviour | - Resting Behaviour | X1DpyS5FN3T | TEXT | INDOOR OUTDOOR | NO |

The Insecticide resistance section registers if there is insecticide resistance in the area and to which insecticide.

| Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Insecticide Resistance | - Malaria Proven insecticide resistance | fyjPqlHE7Dn | BOOLEAN |  | NO |
| Insecticide Resistance | - Malaria Insecticide Name | UFTvUJIMiH0 | TEXT | Only appears if YES is previously selected.BENDIOCARB01 CARBOSULFAN04 DDT4 DIELDRIN4 MALATHION5 PIRIMPHOS025 DELTAMETHRIN005 | NO |

The classification section lets the health worker register the focus status and how it is classified based on the evidence gathered. For the next investigation, this value will be available in the data elements at the beginning of the form.

| Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Classification | - Focus final classification | fjdU9F6EngS | TEXT | ACTIVE RESIDUAL_NON-ACTIVE CLEARED | YES |
| Classification | - Focus date of classification | bl7EMKxJIIT | DATE |  | YES |
| Classification | - Additional Information Evidence | PILB3GtIwiJ | TEXT |  | NO |

### 4.2.3 Foci Response stage

| Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Foci Response | Date of foci response | uvMKOn1oWvd | DATE |  | YES |
| Foci Response | - Households included | k0rev4WSffi | INTEGER_POSITIVE |  | NO |
| Foci Response | - People included | DX4LVYeP7bw | INTEGER_POSITIVE |  | NO |

| Section | TEA / DE / eventDate | UID | valueType | optionSet | mandatory |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Vector Control | MAL- Follow-up Vector Control Intervention - LLIN Distribution | JhpYDsTUfi2 | YES_ONLY |  | NO |
| Vector Control | MAL- Follow-up Vector Control Intervention - INDOOR Residual Spraying | yhX7ljWZV9q | YES_ONLY |  | NO |
| Vector Control | - Follow-up Vector Control Intervention - Larval Source Management | c2c62aRFIfr | YES_ONLY |  | NO |

## Validation rules / Program rules

## Validation rules for malaria Case Surveillance

| _ **name** _ | _ **id** _ | _ **description** _ | _ **condition** _ |
| --- | --- | --- | --- |
| _Assign event date to Diagnosis date Data Element - Diagnosis and treatment_ | _DkNSQkPFdRe_ | _Assigns the event date from the stage feature to the to diagnosis date Data Element - Diagnosis and treatment - this is so that it can be moved to other stages._ | _TRUE_ |
| _Assign value from admission status if admission has value in diagnosis stage_ | _PDZeegogWhP_ | _If admission status has value in diagnosis stage, add there, this allows for calculation of inpatient deaths_ | _d2:hasValue( &#39;Admitted\_previous&#39; )_ |
| _Assign value from detection setting if detection setting has value_ | _kGe41u6HxR4_ | _If Detection setting has a value in the diagnosis stage,add it here_ | _d2:hasValue( &#39;DetectionSettingNewestDiagnosis&#39; )_ |
| _Assign value from Species identified if species has value in diagnosis stage_ | _LXpKv2W5fi2_ | _If species has value in diagnosis stage, add in investigation, this allows for calculation of inpatient deaths_ | _d2:hasValue( &#39;MalariaSpecies&#39; )_ |
| _Assign value of date of completion to date of notification_ | _Co9AGieq1lZ_ | _If there is no value in the notification date, add the date of completion_ | _!d2:hasValue( &#39;notification\_date&#39; )_ |
| _Assign value to diagnosis date from previous event - Case Investigation_ | _o1I4C1t0m6x_ | _If the case investigation stage has a date of diagnosis, add it to the DE in this stage (Hidden section)_ | _d2:hasValue(#{Diagnosis\_date\_previous} )_ |
| _Assign value to diagnosis date from previous event - Focus routine investigation_ | _JizPUKOPn9N_ | _Assign value to diagnosis date from previous event - Focus routine investigation (Hidden Section)_ | _d2:hasValue(#{Diagnosis\_date\_previous} )_ |
| _Case classified as : display as indicator_ | _nmNzVmTYZOb_ | _Display the results of the malaria case classification in the indicator widget_ | _d2:hasValue(&#39;CaseClassifiedAs&#39;)_ |
| _Date of birth : assign age in years_ | _woDbRbosGCn_ | _Assign the age in years based on the difference between the selected date of birth and the enrollment date into the program_ | _d2:hasValue( A{dateofbirth} )_ |
| _Detection setting: proactive not selected_ | _vvxaCLtSXqI_ | _Hide Reason for conducting foci investigation if detection setting != &quot;Proactive (ACD)&quot;_ | _#{DetectionSetting} == &#39;&#39; || #{DetectionSetting} == &#39;PASSIVE&#39; || #{DetectionSetting} == &#39;REACTIVE&#39;_ |
| _Hide Detection setting if no value in diagnosis_ | _gUJMdn2k9q0_ | _If Detection setting does not have a value in the diagnosis stage, hide it here._ | _d2:hasValue( &#39;DetectionSettingNewestDiagnosis&#39; ) == false_ |
| _Hide Section for indicator purposes in case Investigation and classification_ | _nXiXXY2Syhc_ | _Hide Section for indicator purposes in case Investigation and classification_ | _TRUE_ |
| _Hide section for indicator purposes in case outcome stage_ | _bt2DABwwFbZ_ | _we need to transfer value to a DE in this section from a different section_ | _TRUE_ |
| _Hide section for indicator purposes in Diagnosis stage_ | _TgZZ29X7wDS_ | _Hide Section for indicator purposes in case Investigation and classification_ | _TRUE_ |
| _IF Microscopy is selected then HIDE Mixed_ | _a81cE9cycNk_ | _IF Microscopy is selected then HIDE Mixed_ | _#{DIAGNOSIS} == &#39;MICROSCOPY&#39;_ |
| _If RDT selected then HIDE p-Ovale and P. Malariae_ | _fdKz1gGZe4w_ | | _#{DIAGNOSIS} == &#39;RDT&#39;_ |
| _Indoor residual spraying : not conducted_ | _SFNzLxobTyL_ | _Hide the number of houses sprayed if no houses are sprayed_ | _#{IndoorResidualSpraying}!= true_ |
| _LLIN distribution : not conducted_ | _cQRB9WLtnRj_ | _Hide the number of nets distributed if no nets are distributed_ | _#{LLINdistribution} != true_ |
| _Location of investigation != Household then hide household_ | _tK7B2BFBdmI_ | _Location of investigation != Household then hide household_ | _#{MalariaLocation} != &#39;HOUSEHOLD&#39;_ |
| _Malaria history : no history of malaria_ | _tMawDoGpOlz_ | _Hide related fields if the case has no history of malaria_ | _!#{malariahistory}_ |
| _Malaria species type != Other_ | _eyawANeGsf4_ | _Hide the other species type field if the malaria species type is blank or != Other_ | _#{MalariaSpecies} == &#39;&#39; || #{MalariaSpecies} == &#39;PF&#39; || #{MalariaSpecies} == &#39;PV&#39; || #{MalariaSpecies} == &#39;MIX&#39; || #{MalariaSpecies} == &#39;PO&#39; || #{MalariaSpecies} == &#39;PM&#39;_ |
| _Malaria species type : display as indicator_ | _P2WqApkndXb_ | _Display the results of the malaria species type as identified by the malaria test in the indicator widget_ | _d2:hasValue(&#39;MalariaSpecies&#39;)_ |
| _Reason for conduction case investigation != Other_ | _XPkmjVblOJU_ | _Hide the field for other reason for conducting case investigation if other is not selected_ | _#{ReasonCaseInvestigation} == &#39;&#39; || #{ReasonCaseInvestigation} == &#39;DEVELOPMENT\_OF\_ACTIVITIES&#39; || #{ReasonCaseInvestigation} == &#39;POPULATION\_MOVEMENT&#39; || #{ReasonCaseInvestigation} == &#39;REFUGEE\_CRISIS&#39; || #{ReasonCaseInvestigation} == &#39;CLIMATIC\_TRIGGERS&#39;_ |
| _Referred : false_ | _IkvodVu4vZ3_ | _Hide reason for referral if a referral was not made_ | _#{Referred} != &#39;REFERRED&#39;_ |
| _Residents positive for malaria \&gt; Residents tested for malaria_ | _JVzsxIkGzAK_ | _Residents positive for malaria \&gt; Residents tested for malaria_ | _(d2:hasValue(&#39;HHMalariaTest&#39;) &amp;&amp; d2:hasValue(&#39;HHMalariaPositive&#39;)) &amp;&amp; (#{HHMalariaPositive} \&gt; #{HHMalariaTest})_ |
| _Residents tested for malaria \&gt; Residents in household_ | _nMmnj4Nb2vc_ | _Residents tested for malaria \&gt; Residents in household_ | _(d2:hasValue(&#39;HHMalariaTest&#39;) &amp;&amp; d2:hasValue(&#39;HHResidents&#39;)) &amp;&amp; (#{HHMalariaTest} \&gt; #{HHResidents})_ |
| _Residents who own a bed net \&gt; Residents in household_ | _mfRXzxXthu2_ | _Show warning if the Residents who slept under net the previous night \&gt; Residents in household_ | _(d2:hasValue(&#39;HHownbednet&#39;) &amp;&amp; d2:hasValue(&#39;HHResidents&#39;)) &amp;&amp; (#{HHownbednet} \&gt; #{HHResidents})_ |
| _Residents who slept under net the previous night \&gt; Residents in household_ | _lcpfnocmJ8z_ | _Show warning if the Residents who slept under net the previous night \&gt; Residents in household_ | _(d2:hasValue(&#39;HHSleptUnderNet&#39;) &amp;&amp; d2:hasValue(&#39;HHResidents&#39;)) &amp;&amp; (#{HHSleptUnderNet} \&gt; #{HHResidents})_ |
| _Sex : female, Age \&lt;= 13_ | _hhsVY8oobaz_ | _Hide pregnancy status and pregnancy months when the person is female and \&lt;= 13_ | _A{Sex} == &#39;FEMALE&#39; &amp;&amp; (d2:yearsBetween(A{dateofbirth}, V{current\_date}) \&lt;= 13)_ |
| _Sex : is not male_ | _L7XfyMC25Av_ | _Hide pregnancy status fields when the person is male or the field is blank_ | _A{Sex} != &#39;FEMALE&#39;_ |
| _Symptom onset date should be less or equal to date of diagnosis_ | _bgcHuAXU2zw_ | _Shows waning if symptom onset date is less or equal to date of diagnosis_ | _#{symptom\_onset\_date} \&gt; V{event\_date}_ |
| _Symptoms set days with symptoms from onset date_ | _DrYcwLbT2il_ | _Calculates the number of days with symptoms based on the date of the event and symptoms onset date_ | _d2:hasValue(&#39;symptom\_onset\_date&#39;) &amp;&amp; !d2:hasValue(&#39;days\_with\_symptoms&#39;) &amp;&amp; (#{symptom\_onset\_date} \&lt;= V{event\_date}) &amp;&amp; #{symptom\_onset\_date} != &#39;&#39;_ |
| _Symptoms set negative days with symptoms for onset date_ | _WFYSQidLXEf_ | _Assign days with symptoms as a negative value for calculating onset date_ | _d2:hasValue(&#39;days\_with\_symptoms&#39;)_ |
| _Symptoms set onset date from days with symptoms_ | _jsVq7Xj8g9c_ | _Calculates the onset date based on the number of days with symptoms and the date of the event_ | _!d2:hasValue(&#39;symptom\_onset\_date&#39;) &amp;&amp; d2:hasValue(&#39;days\_with\_symptoms&#39;)_ |
| _Tested by : any value and Species type : null_ | _Xc2gb715H50_ | _If the case is tested for confirmation, there must be a species type identified_ | _d2:hasValue(&#39;TestedBy&#39;) &amp;&amp; #{MalariaSpecies} == &#39;&#39;_ |
| _Tested by : display as indicator_ | _amqPvJ3L7oK_ | _Display the malaria test that was performed in the indicator widget_ | _d2:hasValue(&#39;TestedBy&#39;)_ |
| _Tested by : microscopy not selected_ | _PynNbDcsdVU_ | _Hide related fields to Diagnosis by if Diagnosis by != microscopy_ | _#{TestedBy} != &#39;MICROSCOPY&#39;_ |
| _Tested by : no value selected_ | _YZgB6IybcL1_ | _Hide malaria test result and malaria species type of the tested by field is not filled in_ | _#{TestedBy} == &#39;&#39;_ |
| _Tested by : other not selected_ | _mcwkeTxUN67_ | _Hide related fields to Diagnosis by if Diagnosis by != other_ | _#{TestedBy} != &#39;OTHER&#39;_ |
| _Travel outside hide 1st night_ | _reNaR4EK74H_ | _If you marked no or null on &quot;recent travel outside country&quot; then hide first night_ | _#{Travel Outside Country} == &#39;&#39; || #{Travel Outside Country} == &#39;NO&#39;_ |
| _Travel outside hide country name_ | _uDti9DthV1h_ | _If you marked no or null on &quot;recent travel outside country&quot; then hide travel country name_ | _#{Travel Outside Country} == &#39;&#39; || #{Travel Outside Country} == &#39;NO&#39;_ |
| _Travel outside hide last month_ | _Rreg3r1JiBh_ | _If you marked no or null on &quot;recent travel outside country&quot; then hide travel within the last 30 days_ | _#{Travel Outside Country} == &#39;&#39; || #{Travel Outside Country} == &#39;NO&#39;_ |
| _Travel outside hide last night_ | _aqtkn2WKrqq_ | _If you marked no or null on &quot;recent travel outside country&quot; then hide last night_ | _#{Travel Outside Country} == &#39;&#39; || #{Travel Outside Country} == &#39;NO&#39;_ |
| _Travel outside hide region district_ | _kdeJT5Otwsc_ | _If you marked no or null on &quot;recent travel outside country&quot; then hide region district_ | _#{Travel Outside Country} == &#39;&#39; || #{Travel Outside Country} == &#39;NO&#39;_ |
| _Travel outside hide town village_ | _Fj82yKhmYJN_ | _If you marked no or null on &quot;recent travel outside country&quot; then hide town village_ | _#{Travel Outside Country} == &#39;&#39; || #{Travel Outside Country} == &#39;NO&#39;_ |
| _Travel within hide first night_ | _WTGf4T1so2J_ | _If you marked no or null on &quot;recent travel within country&quot; then hide first night_ | _#{Recent Travel Within Country} == &#39;&#39; || #{Recent Travel Within Country} == &#39;NO&#39;_ |
| _Travel within hide last month_ | _tqFHykJ37zJ_ | _If you marked no or null on &quot;recent travel within country&quot; then hide travel within the last 30 days_ | _#{Recent Travel Within Country} == &#39;&#39; || #{Recent Travel Within Country} == &#39;NO&#39;_ |
| _Travel within hide Last night_ | _JcgCZeirV6n_ | _If you marked no or null on &quot;recent travel within country&quot; then hide last night_ | _#{Recent Travel Within Country} == &#39;&#39; || #{Recent Travel Within Country} == &#39;NO&#39;_ |
| _Travel within hide Region/District_ | _zsgZLubWrms_ | _If you marked no or null on &quot;recent travel within country&quot; then hide Region/District_ | _#{Recent Travel Within Country} == &#39;&#39; || #{Recent Travel Within Country} == &#39;NO&#39;_ |
| _Travel within hide Town/village_ | _p0kqW6hTYde_ | _If you marked no or null on &quot;recent travel within country&quot; then hide town/Village_ | _#{Recent Travel Within Country} == &#39;&#39; || #{Recent Travel Within Country} == &#39;NO&#39;_ |

## 5.2 Validation rules for Malaria Foci Investigation and response

| name | id | description | condition |
| --- | --- | --- | --- |
| Assign value date of previous focus classification | nkd671Zt84p | It shows the last date the focus was classified | d2:hasValue( &#39;date\_of\_classification\_previous&#39; ) == true |
| Development activity: null | dCKxEP5bGvh | Hide the development activity selection if there is no development activity present | !#{DevelopmentActivity} |
| Display a Check next to previous Indoor residual spraying if it was previously selected as an action | ITYLhBRfOZA | Display a Check next to previous Indoor residual spraying if was previously selected as an action | d2:hasValue( &#39;Indoor residual Spraying PREVIOUS&#39; ) |
| Display a Check next to previous Larval Source Management if it was previously selected as an action | WhQGnsfxs7j | Display a Check next to previous Larval Source Management if was previously selected as an action | d2:hasValue( &#39;Larval Source Management PREVIOUS&#39; ) |
| Display a Check next to previousLLIN if LLIN was previously selected as an action | HuhD0jX9ARr | Display a Check next to previous LLIN if LLIN was previously selected as an action | d2:hasValue( &#39;LLIN PREVIOUS&#39; ) |
| Display vector classification | Ogo0Ciuybz3 | If a vector was classified previously, this will show that classification | d2:hasValue( &#39;Previous Focus Classification&#39; ) |
| Foci classification : display as indicator | TxkEg880fsw | Display the results of the foci classification in the indicator widget | d2:hasValue(&#39;FociClassification&#39;) |
| Hide &quot;Development activity other specify&quot; | QqQxy5JKBt2 | Unless &quot;Development activity= Other&quot;, hide &quot;Development activity other specify&quot; | #{Development activity Other} == &#39;&#39; || #{Development activity Other} == &#39;AGRICULTURE&#39; || #{Development activity Other} == &#39;CONSTRUCTION&#39; || #{Development activity Other} == &#39;MINING&#39; || #{Development activity Other} == &#39;PLANTATION&#39; |
| Hide &quot;Population type specify other&quot; | IAWNVLOF8Rd | If population type &quot;other&quot; is not selected, hide &quot;Population type specify other&quot; | !d2:hasValue(&#39;PopulationTypeOther&#39;) || !#{PopulationTypeOther} |
| Hide focus status section if no previous status | mIDKsALzkMc | If there was not a focus status previously registered, then the section called &quot;Focus status&quot; does not appear. Typically when it&#39;s the first investigation conducted.
 | d2:hasValue( &#39;date\_of\_classification\_previous&#39; ) == false || d2:hasValue( &#39;date\_of\_classification\_previous&#39; ) == false |
| Hide insecticide list if not proven resistant to insecticides | eEgli5CXC9g | If it | #{insecticide\_resistance\_proven} != true |
| If zero houses visited, hide Vector control section | khygXEKXJSe |
 | #{households\_visited} == 0 |

##


## Analytics

## Dashboards

The package includes seven dashboards, 6 of them are based exclusively on indicators from MAL-CS, the remaining one has a combination of Indicators from MAL-CS and MAL-FOCI. A number has been added to their name to keep them in a logical order and they are prefixed with the respective programme.

##

### _MAL-CS- 01 Trends_

### ![](RackMultipart20211119-4-1qe0v2k_html_fc87ac26d76d817.png)

### MAL-CS-02 Epidemiology

![](RackMultipart20211119-4-1qe0v2k_html_53409dd2aa06f5d3.png)

##

### MAL-CS-03 Treatment and Diagnostic

##

## ![](RackMultipart20211119-4-1qe0v2k_html_beb64b0993f1ad85.png)

##

### MAL-CS-04 Case Notification &amp; Investigation

##

## ![](RackMultipart20211119-4-1qe0v2k_html_142b4bd8ff997bf7.png)

##

### MAL-CS-05- Case Classification

## ![](RackMultipart20211119-4-1qe0v2k_html_a1687c77b462acc5.png)

##

### MAL-CS-06- Geolocation

##

## ![](RackMultipart20211119-4-1qe0v2k_html_31e5e89a81c5b84d.png)

MAL-FOCI

 ![](RackMultipart20211119-4-1qe0v2k_html_6bbb82852212866e.png)

##

## Indicators and Program Indicators

The indicators on this package have been built based on specifications from guiding documents from the WHO. Due to limitations on calculating indicators based on data from multiple events, some programme rules have been used to move data into &quot;hidden sections&#39;&#39; throughout the program. When modifying the package, extra care should be taken that the data elements in these hidden sections are being populated correctly. This can be tested directly in Tracker by removing the program rules which hide the sections. The rules for this are all called &quot;_Hide Section for indicator purposes&quot;. In DHIS2, we differentiate between &quot;Program indicators&quot;, which are based on counting events or enrollments based on a filter, and &quot;Indicators&quot; which are constructed with a numerator and denominator. In most cases for this program, we are using program indicators to create the indicators.

 6.1 Program Indicators:_

| _ **pi\_name** _ | _ **pi\_shortname** _ | _ **pi\_desc** _ | _ **pi\_filter** _ |
| --- | --- | --- | --- |
| _Age 0-5_ | _Age 0-5_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&gt;=0 &amp;&amp; d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&lt;6_ |
| _Age 16-26_ | _Age 16-26_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&gt;=16 &amp;&amp; d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&lt;27_ |
| _Age 27-37_ | _Age 27-37_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&gt;=27 &amp;&amp; d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&lt;38_ |
| _Age 38-49_ | _Age 38-49_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&gt;=38 &amp;&amp; d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&lt;50_ |
| _Age 50-60_ | _Age 50-60_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&gt;=50 &amp;&amp; d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&lt;61_ |
| _Age 6-16_ | _Age 6-16_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&gt;=6 &amp;&amp; d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&lt;16_ |
| _Age 61-71_ | _Age 61-71_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&gt;=61 &amp;&amp; d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&lt;72_ |
| _Age 72-82_ | _Age 72-82_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&gt;=72 &amp;&amp; d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&lt;83_ |
| _Age 83-93_ | _Age 83-93_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&gt;=83 &amp;&amp; d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&lt;94_ |
| _Age 94-104_ | _Age 94-104_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&gt;=94 &amp;&amp; d2:yearsBetween(A{NI0QRzJvQ0k} , V{enrollment\_date})\&lt;104_ |
| _MAL-CS- Active case detection_ | _Active Case detection_ | _Detection by health workers of malaria cases at community and household levels, sometimes in population groups that are considered at high risk. Active case detection can consist of screening for fever followed by parasitological examination of all febrile patients or as parasitological examination of the target population without prior screening for fever._ | _#{hYyB7FUS5eR.fazCI2ygYkq} == &#39;PROACTIVE&#39; || #{hYyB7FUS5eR.fazCI2ygYkq} == &#39;REACTIVE&#39;_ |
| _MAL-CS- Case investigated_ | _Malaria Case investigated_ |
 | _d2:hasValue(#{wYTF0YCHMWr.fazCI2ygYkq})_ |
| _MAL-CS- Cases classified_ | _Malaria Cases classified_ | _Number of cases classified as either indigenous, introduced, imported or induced_ | _(#{eHvTba5ijAh.y3CG06h1Clh}==&#39;IMPORTED&#39;||__#{eHvTba5ijAh.y3CG06h1Clh}==&#39;INTRODUCED&#39;||#{eHvTba5ijAh.y3CG06h1Clh}==&#39;INDUCED&#39;||#{eHvTba5ijAh.y3CG06h1Clh} == &#39;INDIGENOUS&#39;||#{eHvTba5ijAh.y3CG06h1Clh} == &#39;RECRUDESCENT&#39;) &amp;&amp; V{program\_stage\_id}==&#39;eHvTba5ijAh&#39;_ |
| _MAL-CS- Cases detected through PCD_ | _Cases detected through PCD_ | _Number of cases detected through Passive case detection_ | _#{hYyB7FUS5eR.fazCI2ygYkq} == &#39;PASSIVE&#39;_ |
| _MAL-CS- Cases diagnosed last 24 hours_ | _Cases last 24 hours_ | _Number of cases diagnosed in the previous 24 hours_ | _d2:daysBetween(V{event\_date},V{analytics\_period\_end}) == 0 &amp;&amp;_
_d2:hasValue(#{hYyB7FUS5eR.fazCI2ygYkq})_ |
| _MAL-CS- Cases due to mixed infection_ | _Malaria cases mixed_ | _A malaria infection caused by more than one species of plasmodium detected by RDT, microscopy or a molecular test_ | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;MIX&#39;_ |
| _MAL-CS- Cases tested by microscopy_ | _Case tested by microscopy_ | _The number of suspected malaria cases tested by Microscopy_ | _#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; &amp;&amp; V{program\_stage\_id} == &#39;hYyB7FUS5eR&#39;_ |
| _MAL-CS Confirmed cases investigated in N2 days (3 days)_ | _Cases reported within 3 days_ | _Number of confirmed (PCD) malaria cases investigated within (N2),the number of days after confirmation, defined in the national guideline_ | _((V{program\_stage\_id} == &#39;hYyB7FUS5eR&#39; &amp;&amp; d2:daysBetween(V{enrollment\_date},V{event\_date}) \&lt;4) &amp;&amp;_
_d2:hasValue(#{hYyB7FUS5eR.fazCI2ygYkq}) ) &amp;&amp; #{hYyB7FUS5eR.fazCI2ygYkq} == &#39;PASSIVE&#39;_ |
| _MAL-CS- Confirmed cases with symptoms tested with either microscopy or RDT within 24 hours of patient presentation to the health facility_ | _Cases tested with microscopy or RDT in 24h_ | _N: Number of confirmed cases with symptoms tested with either microscopy or RDT within 24 hours of patient presentation to the health facility_ | _V{program\_stage\_id} == &#39;hYyB7FUS5eR&#39; &amp;&amp; d2:daysBetween(V{event\_date},#{hYyB7FUS5eR.fPbtS7glDT2}) \&lt;2 &amp;&amp; (#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; || #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;)_ |
| _MAL-CS- Confirmed malaria cases_ | _Confirmed malaria cases_ | _A case due to mosquito-borne transmission and is acquired outside the area in which it was detected, in a known malarious area to or from which the patient has travelled outside the elimination area_ | _d2:hasValue(#{hYyB7FUS5eR.qdjVZojEK8S}) &amp;&amp; V{program\_stage\_id}==&#39;hYyB7FUS5eR&#39;_ |
| _MAL CS- Confirmed malaria cases investigated within N2 days_ | _Confirmed malaria cases investigated in N2 days_ | _Number of confirmed malaria cases investigated within (N2),the number of days after confirmation, defined in the national guideline (3 days)_ | _d2:daysBetween(V{event\_date},#{wYTF0YCHMWr.ObiXORrILyV}) \&lt; 4_ |
| _MAL-CS- Confirmed with a known species_ | _Confirmed with known species_ |
 | _d2:hasValue(#{hYyB7FUS5eR.vGxpKVMkmaW})_ |
| _MAL-CS- Female_ | _Female_ | _Female cases_ | _A{oindugucx72} == &#39;FEMALE&#39;_ |
| _MAL-CS- Foci investigated within N3 days of diagnosis_ | _Foci investigated within N3 days of diagnosis_ |
 | _d2:daysBetween(#{KwrBvn1EJT3.ObiXORrILyV},V{event\_date}) \&lt;= 3_ |
| _MAL-CS- Foci with response within N7 days of diagnosis_ | _Foci with response within N7 days of diagnosis_ | _N: Number of case notifications received within N1 (24h) of diagnosis_ | _(V{program\_stage\_id} == &#39;KwrBvn1EJT3&#39; &amp;&amp; d2:hasValue(#{KwrBvn1EJT3.ObiXORrILyV}) &amp;&amp; d2:hasValue(#{KwrBvn1EJT3.G7f2D1vl3fD}) &amp;&amp; d2:daysBetween(#{KwrBvn1EJT3.ObiXORrILyV},#{KwrBvn1EJT3.G7f2D1vl3fD}) \&lt;= 7)_ |
| _MAL-CS- Imported_ | _Imported malaria cases_ | _Confirmed malaria cases classified as imported. A case due to mosquito-borne transmission and is acquired outside the area in which it was detected, in a known malarious area to or from which the patient has travelled outside the elimination area_ | _#{wYTF0YCHMWr.bcGuRgKDZei} == &#39;IMPORTED&#39;_ |
| _MAL-CS- Indigenous (Local)_ | _Indigenous malaria cases_ | _Confirmed malaria cases classified as indigenous - A case contracted locally with no evidence of importation and no direct link to transmission from an imported case_ | _#{eHvTba5ijAh.y3CG06h1Clh}== &#39;INDIGENOUS&#39; || #{eHvTba5ijAh.y3CG06h1Clh} == &#39;INTRODUCED&#39;_ |
| _MAL-CS- Induced_ | _Induced_ | _Cases not due to mosquito-borne transmission e.g blood transfusion or congenital malaria_ | _#{wYTF0YCHMWr.bcGuRgKDZei} == &#39;INDUCED&#39;_ |
| _MAL-CS- inpatient_ | _MAL-CS- inpatient case_ |
 | _#{hYyB7FUS5eR.MKMyvXshCdB}== &#39;ADMITTED&#39;_ |
| _MAL-CS- inpatient deaths_ | _inpatient deaths_ |
 | _#{eHvTba5ijAh.MKMyvXshCdB} == &#39;ADMITTED&#39; &amp;&amp; #{eHvTba5ijAh.zXNfOKXRBA9} == &#39;DIED&#39;_ |
| _MAL-CS- Introduced_ | _Introduced_ | _Confirmed malaria cases classified as introduced. A case contracted locally, with strong epidemiological evidence linking it directly to a known imported case (first-generation local transmission). First-generation local transmission; epidemiologically linked to proven imported case_ | _#{wYTF0YCHMWr.bcGuRgKDZei} == &#39;INTRODUCED&#39;_ |
| _MAL-CS- Malaria age current (months)_ | _Malaria age current (months)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k},V{current\_date})\&lt;1_ |
| _MAL-CS Malaria age current (years)_ | _Malaria age current (years)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k},V{current\_date}) \&gt; 0_ |
| _MAL-CS- Malaria cases (All registered)_ | _All Malaria Cases_ |
 | _TRUE_ |
| _MAL-CS- Malaria death_ | _Malaria death_ |
 | _#{eHvTba5ijAh.zXNfOKXRBA9} == &#39;DIED&#39; &amp;&amp; V{program\_stage\_id} == &#39;eHvTba5ijAh&#39;_ |
| _MAL-CS- Malaria test - RDT_ | _Malaria test - RDT_ | _The number of suspected malaria cases tested by RDT_ | _#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- Male_ | _Male_ |
 | _A{oindugucx72} == &#39;MALE&#39;_ |
| _MAL-CS- microscopy 0-4 years female_ | _microscopy (f 0-4)_ | _The number of suspected malaria cases tested by Microscopy with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;FEMALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- microscopy 0-4 years male_ | _microscopy (m 0-4)_ | _The number of suspected malaria cases tested by Microscopy with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;MALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- microscopy 15+ years female_ | _microscopy (f 15+)_ | _The number of suspected malaria cases tested by Microscopy with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;FEMALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- microscopy 15+ years male_ | _microscopy (m 15+)_ | _The number of suspected malaria cases tested by Microscopy with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;MALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- microscopy 5-14 years female_ | _microscopy (f 5-14)_ | _The number of suspected malaria cases tested by Microscopy with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;FEMALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- microscopy 5-14 years male_ | _microscopy (m 5-14)_ | _The number of suspected malaria cases tested by Microscopy with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;MALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- microscopy (other)_ | _mic (other)_ |
 | _#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; and #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;OTHER&#39;_ |
| _MAL-CS- microscopy Pf._ | _microscopy Pf._ |
 | _#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; and #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39;_ |
| _MAL-CS- microscopy Pf. 0-4 years female_ | _microscopy (Pf., f 0-4)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;FEMALE&#39;and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; and #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39;_ |
| _MAL-CS- microscopy Pf. 0-4 years male_ | _microscopy (Pf., m 0-4)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;MALE&#39;and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; and #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39;_ |
| _MAL-CS- microscopy Pf. 15+ years female_ | _microscopy (Pf., f 15+)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;FEMALE&#39;and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; and #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39;_ |
| _MAL-CS- microscopy Pf. 15+ years male_ | _microscopy (Pf., m 15+)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;MALE&#39;and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; and #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39;_ |
| _MAL-CS- microscopy Pf. 5-14 years female_ | _microscopy (Pf., f 5-14)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;FEMALE&#39;and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; and #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39;_ |
| _MAL-CS- microscopy Pf. 5-14 years male_ | _microscopy (Pf., m 5-14)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;MALE&#39;and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; and #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39;_ |
| _MAL-CS- Mixed_ | _Mixed_ |
 | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;MIX&#39;_ |
| _MAL-CS- Mixed RDT_ | _Mixed RDT_ |
 | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;MIX&#39; &amp;&amp;__#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- Nationality: BY COUNTRY_ | _NATIONALITY: BY COUNTRY_ | _One PI per country based on attribute &quot;Nationality&quot;_ | _A{spkM2E9dn2J} == &#39;AF&#39;_ |
| _MAL-CS- Newly diagnosed_ | _Newly diagnosed_ | _Number of newly diagnosed malaria cases during a defined period in a specified population_ | _d2:daysBetween(V{enrollment\_date}, V{analytics\_period\_start}) \&gt; 0 &amp;&amp; d2:daysBetween(V{enrollment\_date}, V{analytics\_period\_end}) \&lt; 0_ |
| _MAL-CS- Notification received within N1 (24 hs) of diagnosis_ | _Cases notified within 24hs_ | _N: Number of case notifications received within N1 (24h) of diagnosis_ | _(V{program\_stage\_id} == &#39;hYyB7FUS5eR&#39; &amp;&amp; d2:daysBetween(V{event\_date},#{hYyB7FUS5eR.fPbtS7glDT2}) \&lt; 2 &amp;&amp; d2:hasValue(#{hYyB7FUS5eR.fazCI2ygYkq}) &amp;&amp; d2:hasValue(#{hYyB7FUS5eR.qdjVZojEK8S}) )_ |
| _MAL-CS- Not pregnant_ | _Not pregnant_ | _Not pregnant female cases_ | _A{oindugucx72} == &#39;FEMALE&#39; &amp;&amp; (A{sPDKWSQ2vKQ}== &#39;NO&#39; || A{sPDKWSQ2vKQ}== &#39;&#39;)_ |
| _MAL-CS- Number of confirmed Malaria Cases investigated (PCD)_ | _Confirmed cases investigated (PCD)_ | _Number of positive cases detected through PCD and investigated_ | _#{wYTF0YCHMWr.fazCI2ygYkq} == &#39;PASSIVE&#39;_ |
| _MAL-CS- Occupation Farmer_ | _Occupation Farmer_ | _Occupation Farmer_ | _A{ZZmkcCkzzWr} == &#39;FARMER&#39;_ |
| _MAL-CS- Occupation Migrant worker_ | _Occupation Migrant worker_ | _Occupation Migrant worker_ | _A{ZZmkcCkzzWr} == &#39;MIGRANTWORKER&#39;_ |
| _MAL-CS- Occupation Mine Worker_ | _Occupation Mine Worker_ | _Occupation Mine worker_ | _A{ZZmkcCkzzWr} == &#39;MINEWORKER&#39;_ |
| _MAL-CS- Occupation Nurse_ | _Occupation Nurse_ | _Occupation Nurse_ | _A{ZZmkcCkzzWr} == &#39;NURSE&#39;_ |
| _MAL-CS- Occupation Seasonal worker_ | _Occupation Seasonal worker_ | _Occupation Seasonal worker_ | _A{ZZmkcCkzzWr} == &#39;SEASONALWORKER&#39;_ |
| _MAL-CS- Occupation Student_ | _Occupation Student_ | _Occupation Student_ | _A{ZZmkcCkzzWr} == &#39;STUDENT&#39;_ |
| _MAL-CS- Occupation Teacher_ | _Occupation Teacher_ | _Occupation Teacher_ | _A{ZZmkcCkzzWr} == &#39;TEACHER&#39;_ |
| _MAL-CS- Occupation Truck driver_ | _Occupation Truck driver_ | _Occupation Truck driver_ | _A{ZZmkcCkzzWr} == &#39;TRUCKDRIVER&#39;_ |
| _MAL-CS- Other Species (Cases due to)_ | _MAL-CS- Other Species_ |
 | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;OTHER&#39;_ |
| _MAL-CS- outpatient_ | _outpatient_ |
 | _#{hYyB7FUS5eR.MKMyvXshCdB} == &#39;ADMITTED&#39;_ |
| _MAL-CS- Passive case detection_ | _Passive Case detection_ | _Detection by health workers of malaria cases at community and household levels, sometimes in population groups that are considered at high risk. Active case detection can consist of screening for fever followed by parasitological examination of all febrile patients or as parasitological examination of the target population without prior screening for fever._ | _#{hYyB7FUS5eR.fazCI2ygYkq} == &#39;PASSIVE&#39;_ |
| _MAL-CS- Pf. 0-4 years female RDT &amp; Microscopy_ | _Pf., f 0-4_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;FEMALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- Pf. 0-4 years male RDT &amp; Microscopy_ | _(Pf., m 0-4)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;MALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- Pf. 15+ years female RDT &amp; Microscopy_ | _(Pf., f 15+)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;FEMALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- Pf. 15+ years male RDT &amp; Microscopy_ | _Pf., m 15+_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;MALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- Pf. 5-14 years female RDT &amp; Microscopy_ | _Pf., f 5-14_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;FEMALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- Pf. 5-14 years male RDT &amp; Microscopy_ | _Pf., m 5-14_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;MALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P.Falciparum (cases due to) RDT or Microscopy_ | _Pf. RDT or Microscopy_ | _Malaria cases caused by the species P. falciparum, detected either by RDT, microscopy or a molecular test_ | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PF&#39; &amp;&amp; (#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; || #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;)_ |
| _MAL-CS- P.Knowlesi (Cases due to) Microscopy_ | _P.knowlesi case_ | _A malaria case caused by the species P. knowlesi detected by microscopy_ | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PK&#39;_ |
| _MAL-CS- P Malariae. 0-4 years female Microscopy_ | _P Malariae., f 0-4_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;FEMALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PM&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P Malariae. 0-4 years male Microscopy_ | _P Malariae., m 0-4_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;MALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PM&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P Malariae. 15+ years female Microscopy_ | _P Malariae., f 15+_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;FEMALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PM&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P Malariae. 15+ years male Microscopy_ | _P Malariae., m 15+_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;MALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PM&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P Malariae. 5-14 years female Microscopy_ | _P Malariae, f 5-14_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;FEMALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PM&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P Malariae. 5-14 years male Microscopy_ | _P Malariae, m 5-14_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;MALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PM&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P.Malariae (cases due to)_ | _P.Malariae case_ | _Malaria cases caused by the species P. malariae_ | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PM&#39;_ |
| _MAL-CS- P.Malariae (cases due to) Microscopy_ | _P.M Microscopy_ |
 | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PM&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P O. 0-4 years female Microscopy_ | _P O., f 0-4_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;FEMALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PO&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P O. 0-4 years male Microscopy_ | _P O., m 0-4_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;MALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PO&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P O. 15+ years female Microscopy_ | _P O., f 15+_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;FEMALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PO&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P O. 15+ years male Microscopy_ | _P O., m 15+_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;MALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PO&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P O. 5-14 years female Microscopy_ | _(P O, f 5-14)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;FEMALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PO&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P O. 5-14 years male Microscopy_ | _P O, m 5-14_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;MALE&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PO&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- P.Ovale_ | _P.Ovale_ |
 | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PO&#39;_ |
| _MAL-CS- P.Ovale (Cases due to) Microscopy_ | _P O. Microscopy_ |
 | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PO&#39; &amp;&amp; #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;_ |
| _MAL-CS- Pregnant_ | _Pregnant_ | _Female cases_ | _A{sPDKWSQ2vKQ} == &#39;YES&#39;_ |
| _MAL-CS- Proactive case detection_ | _Proactive case detection_ |
 | _#{hYyB7FUS5eR.fazCI2ygYkq} == &#39;PROACTIVE&#39;_ |
| _MAL-CS- Pv. 0-4 years female RDT &amp; Microscopy_ | _microscopy (Pv., f 0-4)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;FEMALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;&amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PV&#39;&amp;&amp;__#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- Pv. 0-4 years male RDT &amp; Microscopy_ | _microscopy (Pv., m 0-4)_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;MALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PV&#39; &amp;&amp;__#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- Pv. 15+ years female RDT &amp; Microscopy_ | _Pv., f 15+ RDT &amp; Microscopy_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;FEMALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PV&#39; &amp;&amp;__#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- Pv. 15+ years male RDT &amp; Microscopy_ | _Pv., m 15+ RDT &amp; Microscopy_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;MALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PV&#39; &amp;&amp;__#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- Pv. 5-14 years female RDT &amp; Microscopy_ | _Pv., f 5-14 RDT &amp; Microscopy_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;FEMALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PV&#39; &amp;&amp;__#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- Pv. 5-14 years male RDT &amp; Microscopy_ | _(Pv., m 5-14) RDT &amp; Microscopy_ |
 | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;MALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; &amp;&amp; #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PV&#39; &amp;&amp;__#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- P.vivax_ | _Pv_ |
 | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PV&#39;_ |
| _MAL-CS- P.vivax (cases due to) RDT &amp; microscopy_ | _Pv RDT &amp; microscopy_ |
 | _#{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;PV&#39; &amp;&amp; ( #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39; ||__#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;)_ |
| _MAL-CS- RDT_ | _MAL-CS- RDT case_ | _The number of malaria cases tested by RDT with a positive result_ | _#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- RDT 0-4 years female_ | _RDT (f 0-4)_ | _The number of suspected malaria cases tested by RDT with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;FEMALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- RDT 0-4 years male_ | _RDT (m 0-4)_ | _The number of suspected malaria cases tested by RDT with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;MALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- RDT 15+ years female_ | _RDT (f 15+)_ | _The number of suspected malaria cases tested by RDT with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;FEMALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- RDT 15+ years male_ | _RDT (m 15+)_ | _The number of suspected malaria cases tested by RDT with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;MALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- RDT 5-14 years female_ | _RDT (f 5-14)_ | _The number of suspected malaria cases tested by RDT with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;FEMALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- RDT 5-14 years male_ | _RDT m 5-14_ | _The number of suspected malaria cases tested by RDT with a positive result_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;MALE&#39; and #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39;_ |
| _MAL-CS- RDT+Microscopy_ | _RDT+Microscopy_ | _Total malaria positives cases by Microscopy and RDT_ | _(#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; or #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;)_ |
| _MAL-CS- RDT+Microscopy 0-4 years female_ | _RDT+Microscopy (f 0-4)_ | _Total malaria positives cases by Microscopy and RDT_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;FEMALE&#39; and (#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; or #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;)_ |
| _MAL-CS- RDT+Microscopy 0-4 years male_ | _RDT+Microscopy (m 0-4)_ | _Total malaria positives cases by Microscopy and RDT_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 0 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 5 and A{oindugucx72} == &#39;MALE&#39; and (#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; or #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;)_ |
| _MAL-CS- RDT+Microscopy 15+ years female_ | _RDT+Microscopy (f 15+)_ | _Total malaria positives cases by Microscopy and RDT_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;FEMALE&#39; and (#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; or #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;)_ |
| _MAL-CS- RDT+Microscopy 15+ years male_ | _RDT+Microscopy (m 15+)_ | _Total malaria positives cases by Microscopy and RDT_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 15 and A{oindugucx72} == &#39;MALE&#39; and (#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; or #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;)_ |
| _MAL-CS- RDT+Microscopy 5-14 years female_ | _RDT+Microscopy (f 5-14)_ | _Total malaria positives cases by Microscopy and RDT_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;FEMALE&#39; and (#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; or #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;)_ |
| _MAL-CS- RDT+Microscopy 5-14 years male_ | _RDT+Microscopy (m 5-14)_ | _Total malaria positives cases by Microscopy and RDT_ | _d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&gt;= 5 and d2:yearsBetween(A{NI0QRzJvQ0k}, V{enrollment\_date}) \&lt; 15 and A{oindugucx72} == &#39;MALE&#39; and (#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; or #{hYyB7FUS5eR.qdjVZojEK8S} == &#39;MICROSCOPY&#39;)_ |
| _MAL-CS- RDT (other)_ | _RDT (other)_ |
 | _#{hYyB7FUS5eR.qdjVZojEK8S} == &#39;RDT&#39; and #{hYyB7FUS5eR.vGxpKVMkmaW} == &#39;OTHER&#39;_ |
| _MAL-CS- Reactive case detection_ | _Reactive Case detection_ |
 | _#{hYyB7FUS5eR.fazCI2ygYkq} == &#39;REACTIVE&#39;_ |
| _MAL-FOCI- Foci Classified_ | _Foci classified_ |
 | _(#{CWaAcQYKVpq.fjdU9F6EngS} == &#39;ACTIVE&#39; || #{CWaAcQYKVpq.fjdU9F6EngS} == &#39;RESIDUAL\_NON-ACTIVE&#39;|| #{CWaAcQYKVpq.fjdU9F6EngS} == &#39;CLEARED&#39;)_ |
| _MAL-FOCI- Foci classified as active_ | _Foci active_ |
 | _(#{CWaAcQYKVpq.fjdU9F6EngS} == &#39;ACTIVE&#39; &amp;&amp; V{program\_stage\_id} == &#39;CWaAcQYKVpq&#39;)_ |
| _MAL-FOCI- Foci classified as residual non-active_ | _Foci residual non-active_ |
 | _(#{CWaAcQYKVpq.fjdU9F6EngS} == &#39;RESIDUAL\_NON-ACTIVE&#39; &amp;&amp; V{program\_stage\_id} == &#39;CWaAcQYKVpq&#39;)_ |
| _MAL-FOCI- Foci Identified_ | _Foci Identified_ | _Total number of foci in the registry in a one year period_ | _TRUE_ |
| _MAL-FOCI- Foci investigated_ | _Foci investigations_ |
 | _(d2:hasValue(#{CWaAcQYKVpq.fjdU9F6EngS}) &amp;&amp; V{program\_stage\_id} ==&#39;CWaAcQYKVpq&#39;)_ |
| _MAL-FOCI- Foci Reclassified_ | _Foci Reclassified_ | _Number of foci reclassified in a year_ | _d2:hasValue(#{CWaAcQYKVpq.fjdU9F6EngS}) &amp;&amp; d2:hasValue(#{CWaAcQYKVpq.V1OnhZYfSa2}) &amp;&amp; V{program\_stage\_id} == &#39;CWaAcQYKVpq&#39;_ |
| _MAL-FOCI- Foci Registered_ | _Foci Registered_ | _Total number of foci in the registry_ | _TRUE_ |
| _MAL-FOCI- Foci with response_ | _Foci with response_ | _Number of malaria foci that received any form of response_ | _V{program\_stage\_id} ==&#39;uvMKOn1oWvd&#39;_ |

6.2 Indicators

| **Indicator name** | **Numerator description** | **Denominator description** |
| --- | --- | --- |
| MAL-CS- Case reports received \&lt; 24 h after detection % | Number of case notifications received within 24h of diagnosis | Total number of confirmed malaria case reports |
| MAL-CS- Cases diagnosed with Microscopy (%) | Malaria cases diagnosed by RDT | Total confirmed Malaria cases with a known species |
| MAL-CS- Cases diagnosed with RDT (%) | Malaria cases diagnosed by RDT | Total confirmed Malaria cases with a known species |
| MAL-CS- Cases investigated (%) | Number of cases investigated | Number of positive cases detected through PCD |
| MAL-CS- Cases investigated on time (%) | sum of cases with enrollment date within 3 days from date of diagnosis | Total confirmed cases reported |
| MAL-CS- Cases notified on time (%) | sum of cases enrollment date within 1 day from date of diagnosis | Total confirmed cases reported |
| MAL-CS- Cases notified within N1 days (24 hs) (%) | Number of cases within the time limit specified by national guidelines for time from diagnosis to notification (typically within 24 hrs) | Total number of confirmed malaria cases reported through PCD |
| MAL-CS- Confirmed cases classified (%) | Number of positive cases classified | Number of positive cases detected through PCD and investigated x100 |
| MAL-CS- Confirmed cases investigated (%) | Number of positive cases detected through PCD and investigated | Number of positive cases detected through PCD |
| MAL-CS- Confirmed cases with symptoms diagnosed within 24 hours (%) | N: Number of confirmed cases with symptoms tested with either microscopy or RDT within 24 hours of patient presentation to the health facility | Total number of confirmed malaria cases reported through PCD |
| MAL-CS- Female cases (%) | Malaria female cases | Total confirmed Malaria cases with a known species |
| MAL-CS- Foci investigated within N3 days of diagnosis (%) | Confirmed Malaria Cases | Foci investigated within N3 days of diagnosis |
| MAL-CS- Foci with response within N7 days of diagnosis (%) | N7 | Confirmed Malaria Cases |
| MAL-CS- Imported cases (%) | Number of Imported cases | Confirmed Malaria Cases |
| MAL-CS- Indigenous cases (%) | Number of indigenous cases | Confirmed Malaria Cases |
| MAL-CS- Introduced cases (%) | Number of Introduced cases | Confirmed Malaria Cases |
| MAL-CS- Malaria Case Occupation: Farmer (%) | Farmer | Total confirmed Malaria cases with a known species |
| MAL-CS- Malaria Case Occupation: Migrant Worker (%) | Farmer | Total confirmed Malaria cases with a known species |
| MAL-CS- Malaria Case Occupation: Mine worker (%) | Malaria female cases | Total confirmed Malaria cases with a known species |
| MAL-CS- Malaria Case Occupation: Nurse (%) | Malaria Nurse | Total confirmed Malaria cases with a known species |
| MAL-CS- Malaria Case Occupation: Seasonal worker (%) | Seasonal worker | Total confirmed Malaria cases with a known species |
| MAL-CS- Malaria Case Occupation: Student (%) | Malaria Student | Total confirmed Malaria cases with a known species |
| MAL-CS- Malaria Case Occupation: Teacher (%) | Malaria Student | Total confirmed Malaria cases with a known species |
| MAL-CS- Malaria Case Occupation: Truck Driver (%) | Malaria Student | Total confirmed Malaria cases with a known species |
| MAL-CS- Male cases (%) | Malaria male cases | Total confirmed Malaria cases |
| MAL-CS- Mixed infection cases (%) | Malaria cases due to P.vivax identified by RDT or microscopy | Total confirmed Malaria cases with a known species |
| MAL-CS- P.falciparum cases (%) | Malaria cases due to P.Falciparum | Total confirmed Malaria cases with a known species |
| MAL-CS- P.vivax cases (%) | Malaria cases due to mixed infection | Total confirmed Malaria cases with a known species |
| MAL-CS- Passive case detection (%) | Passive | Total confirmed Malaria cases with a known species |
| MAL-CS- Proactive case detection (%) | Proactive | Total confirmed Malaria cases with a known species |
| MAL-CS- Proportion of imported cases | Imported cases | Total confirmed malaria cases |
| MAL-CS- Proportion of local cases | Local cases (indigenous + introduced) | Total confirmed malaria cases |
| MAL-CS- Reactive case detection (%) | Reactive | Total confirmed Malaria cases with a known species |
| MAL-CS- Timeliness - Case notifications received within (N1) 24h of detection % | Number of case notifications received within 24h of diagnosis | Number of cases reported |
| MAL-CS- Timeliness - Cases investigated within (N2) diagnosis (3 days) % | Number of case notifications received within 24h of diagnosis | Number of cases reported |
| MAL-FOCI- Foci classified (%) | Number of foci classified | Total number of foci in the registry |
| MAL-FOCI- Foci classified as active (%) | Number of foci classified as active | Total number of foci in the registry |
| MAL-FOCI- Foci classified as cleared (%) | Number of foci classified as cleared | Total number of foci in the registry |
| MAL-FOCI- Foci classified as residual non-active (%) | Number of foci classified as residual non-active | Total number of foci in the registry |
| MAL-FOCI- Foci investigated (%) | Number of foci investigated | Total Number of foci recorded in this period |

Note:
 Indicators that calculate a percentage of cases based on detection vs. outcome can show a result exceeding 100%, this results from cases in which the outcome happens in the following period.

## Android compatibility

The program as it stands is fully compatible with Android. When implementing with Android, especially if the program is modified, it is important to be familiar with the Android implementation guide [https://docs.dhis2.org/en/full/implement/dhis2-android-implementation-guide.html](https://docs.dhis2.org/en/full/implement/dhis2-android-implementation-guide.html)
