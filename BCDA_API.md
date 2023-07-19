# Beneficiary Claims Data API Documentation

## Overview

The [**Beneficiary Claims Data API (BCDA)**](https://bcda.cms.gov/) enables Accountable Care Organizations (ACOs) to retrieve Medicare Part A, Part B, and Part D claims data for their assigned beneficiaries. BCDA is currently serving ACOs and other entities participating in the following programs:

- [Medicare Shared Savings Program](https://www.cms.gov/medicare/medicare-fee-for-service-payment/sharedsavingsprogram)
- [ACO Realizing Equity, Access, and Community Health (REACH)](https://innovation.cms.gov/innovation-models/aco-reach)
- [Kidney Care Choices](https://innovation.cms.gov/innovation-models/kidney-care-choices-kcc-model/)

BCDA provides the following benefits to participanting organizations:

1. Supplements ACOs' insight into their assigned beneficiary populations.
2. Enables organizations to make claims data requests more often - either weekly or daily based on the alternative payment model and data type.
3. Offers Medicare claims data in a format that is aligned with the healthcare interoperability standards promoted by the [Office of the National Coordinator (ONC)](https://HealthIT.gov/), the [Centers for Medicare and Medicaid Services (CMS)](https://www.cms.gov/about-cms/obrhi/interoperability) and the standards organizations.

## API Reference

The Beneficiary Claims Data API is organized around the [Representational State Transfer (REST)](http://en.wikipedia.org/wiki/Representational_State_Transfer) architecture and the [Fast Healthcare Interoperability Resources (FHIR)](http://hl7.org/fhir/) specification. The REST API allows you to generate access tokens, request data exports, manage your export jobs, download data in bulk and access the metadata associated with your population of beneficiaries.

### API Versions

The Beneficiary Claims Data API is versioned. There are two versions of the API currently supported. BCDA's versioning strategy is implemented through the [Uniform Resource Identifier (URI)](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) path using the major version number. You would use the following URI path segments to access the two available versions of the API:

- `/api/v1` &mdash; Version 1
- `/api/v2` &mdash; Version 2

**CMS encourages organizations to use Version 2 of the API** in order to benefit from the latest enhancements, FHIR release version and the newest data types and dictionary.

### Benefits of BCDA Version 2

Using the BCDA Version 2 provides to following benefits and features:

- Support for [FHIR Release 4](https://hl7.org/fhir/R4/) (v4.0.1)
- Support for the [CARIN Consumer Directed Payer Data Exchange FHIR Implementation Guide](http://hl7.org/fhir/us/carin-bb/STU2/)[^1] (v2.0.0)
- Support for the [Bulk Data Access FHIR Implementation Guide](http://hl7.org/fhir/uv/bulkdata/STU2/) (v2.0.0)
- Access to weekly updates of the adjudicated claims data
- Access to daily updates of the partially adjudicated claims data (limited to certain alternative payment models)

[^1]: Also known as the _CARIN Implementation Guide for Blue Button_.

#### FHIR Resources

BCDA Version 2 uses five resource types from the FHIR specification to represent demographic, coverage and claims data.

##### Patient

The [Patient](http://hl7.org/fhir/us/carin-bb/STU2/StructureDefinition-C4BB-Patient.html) resource type is used to represent the demographic data of a Medicare beneficiary. This refers to all the non-clinical data about the patient, including: name, date of birth, address, phone number, sex, race, unique identifiers, etc.

##### Coverage

The [Coverage](http://hl7.org/fhir/us/carin-bb/STU2/StructureDefinition-C4BB-Coverage.html) resource type is used to represent the insurance coverage of a Medicare beneficiary, including information about coverage in both Medicare and Medicaid for [dually eligible individuals](https://www.cms.gov/Medicare-Medicaid-Coordination/Medicare-and-Medicaid-Coordination/Medicare-Medicaid-Coordination-Office/Downloads/MMCO_Factsheet.pdf).

##### ExplanationOfBenefit

The [Explanation of Benefit](https://hl7.org/fhir/R4/explanationofbenefit.html) resource type is used to represent adjudicated claims data. This resource includes information like the location and date when the service was performed, the diagnosis codes, the provider information and the cost of care. Depending on the context of the service provided, it could represent the following claim types:

- [Inpatient Institutional Claims](http://hl7.org/fhir/us/carin-bb/STU2/StructureDefinition-C4BB-ExplanationOfBenefit-Inpatient-Institutional.html) (Durable Medical Equipment, Hospital, Hospice, Skilled Nurse Facility)
- [Outpatient Institutional Claims](http://hl7.org/fhir/us/carin-bb/STU2/StructureDefinition-C4BB-ExplanationOfBenefit-Outpatient-Institutional.html) (Institutional Outpatient Providers)
- [Professional Non-Clinician Claims](http://hl7.org/fhir/us/carin-bb/STU2/StructureDefinition-C4BB-ExplanationOfBenefit-Professional-NonClinician.html) (Non-institutional, Home Health Agency)
- [Pharmacy Claims](http://hl7.org/fhir/us/carin-bb/STU2/StructureDefinition-C4BB-ExplanationOfBenefit-Professional-NonClinician.html) (Part D Prescription Drug Events)

##### Claim

The [Claim](https://hl7.org/fhir/R4/claim.html) resource type is used to represent partially adjudicated claims data. These are snapshots of the claims as they go through the Medicare payment processing systems. This resource is used for professional and institutional claims and includes information about the provider submitting the claim and the services provided to the beneficiary.

This resource is only available to participants in the ACO REACH model at this time.

##### ClaimResponse

The [ClaimResponse](https://hl7.org/fhir/R4/claimresponse.html) resource type is used to represent partially adjudicated claims data. These are snapshots of the claims as they go through the Medicare payment processing systems. This resource provides information about the claim's adjudication status and processing outcome.

This resource is only available to participants in the ACO REACH model at this time.

## Sandbox

## Bulk Data Access

## API Endpoints

### Authentication

### Group

### Jobs

### Data

### Attribution Status

