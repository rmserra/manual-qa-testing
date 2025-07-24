**Test plan US-001: User Registration via API**

# Table of Contents

1. [Document Information](#1-document-information)  
   1.1 [Author](#11-author)  
   1.2 [Revision history](#12-revision-history)  
   1.3 [Approval process and reviewers](#13-approval-process-and-reviewers)  

2. [Introduction](#2-introduction)  
   2.1 [Overview](#21-overview)  
   2.2 [Scope](#22-scope)  
   &nbsp;&nbsp;&nbsp;&nbsp;2.2.1 [In scope](#221-in-scope)  
   &nbsp;&nbsp;&nbsp;&nbsp;2.2.2 [Out of scope](#222-out-of-scope)  
   2.3 [Project Information](#23-project-information)  
   2.4 [Schedule and Milestones](#24-schedule-and-milestones)  
   2.5 [Reference material](#25-reference-material)  
   2.6 [Definitions and acronyms](#26-definitions-and-acronyms)  

3. [Testing Strategy](#3-testing-strategy)  
   3.1 [Features to be tested](#31-features-to-be-tested)  
   &nbsp;&nbsp;&nbsp;&nbsp;3.1.1 [User Registration Functionality](#311-user-registration-functionality)  
   &nbsp;&nbsp;&nbsp;&nbsp;3.1.2 [Field Validations](#312-field-validations)  
   &nbsp;&nbsp;&nbsp;&nbsp;3.1.3 [Security Validations](#313-security-validations)  
   &nbsp;&nbsp;&nbsp;&nbsp;3.1.4 [Database Verification](#314-database-verification)  
   3.2 [Features not to be tested](#32-features-not-to-be-tested)  
   3.3 [Deployment scenarios](#33-deployment-scenarios)  
   3.4 [Testing approach](#34-testing-approach)  
   &nbsp;&nbsp;&nbsp;&nbsp;3.4.1 [Test Design Techniques](#341-test-design-techniques)  

4. [Test Environment](#4-test-environment)  
   4.1 [Prerequisites](#41-prerequisites)  
   4.2 [Operating systems](#42-operating-systems)  
   4.3 [Hardware](#43-hardware)  
   4.4 [Software](#44-software)  

5. [Risks and Testing Constraints](#5-risks-and-testing-constraints)  
   5.1 [Risks and Assumptions](#51-risks-and-assumptions)  
   &nbsp;&nbsp;&nbsp;&nbsp;5.1.1 [Risks](#511-risks)  
   &nbsp;&nbsp;&nbsp;&nbsp;5.1.2 [Assumptions](#512-assumptions)  
   5.2 [Testing Constraints](#52-testing-constraints)  
   5.3 [Education](#53-education)  

6. [Sample High-Level Test Cases](#6-sample-high-level-test-cases)  
   6.1 [Successful registration](#61-successful-registration)  
   6.2 [Missing or invalid required fields](#62-missing-or-invalid-required-fields)  
   6.3 [Boundary and format validation](#63-boundary-and-format-validation)  
   &nbsp;&nbsp;&nbsp;&nbsp;6.3.1 [Username length](#631-username-length)  
   &nbsp;&nbsp;&nbsp;&nbsp;6.3.2 [Age validation](#632-age-validation)  
   &nbsp;&nbsp;&nbsp;&nbsp;6.3.3 [Email length](#633-email-length)  
   6.4 [Duplicate entries](#64-duplicate-entries)  
   6.5 [Security validations](#65-security-validations)  
   6.6 [Data integrity](#66-data-integrity)  

# 1. Document Information

## 1.1 Author
| Author             | Email                       | Date       |  
|--------------------|-----------------------------|------------|
| Rosa Micaela Serra | serra.rosamicaela@gmail.com | 30-04-2025 |

## 1.2 Revision history
| Author             | Date       | Version | Description                              |
|--------------------|------------|---------|------------------------------------------|
| Rosa Micaela Serra | 30-04-2025 | 0.1     | Initial version                          |
| Rosa Micaela Serra | 01-05-2025 | 1.0     | Added and completed sections 3,4,5 and 6 |
| Rosa Micaela Serra | 07-05-2025 | 2.0     | Final version                            |

## 1.3 Approval process and reviewers
The document will be reviewed by the QA team and PO. Final approval will be granted based on consensus during scheduled review sessions.

# 2. Introduction
## 2.1 Overview
This test plan covers both functional and non-functional testing of the POST /users API  endpoint, which allows user registration by submitting user’s personal information. The  primary objective is to ensure that the account creation process functions correctly,  securely, and in compliance with the established requirements and acceptance  criteria. 
The testing strategy includes: 
- Functional testing to verify that all expected behaviors (for successful  registration, error handling and response structure) work as intended.
- Validation testing to ensure that all required fields are correctly validated, with  appropriate handling of missing or invalid inputs. 
- Security testing focused on password encryption, input sanitization, and  prevention of common vulnerabilities (such as SQL injection or XSS).
- Database verification to confirm that user data is accurately and securely  stored, and consistent across the system.

## 2.2 Scope
### 2.2.1 In scope
This test plan focuses on validating the behavior and security of the POST /users API endpoint, specifically related to user registration. The following items are considered in  scope: 

- Functional testing of the POST /users endpoint for user registration
- Validation of required and optional fields, including:
  - username, email, password, age (required fields)
  - phone (optional fields)
- Verification of input validation rules, including:
  - username: uniqueness, allowed characters, and length boundaries (5–30  characters)
  - email: valid format and uniqueness
  - age: must be a number within the 18–60 range
  - password: must meet complexity requirements (e.g. minimum length, at  least one uppercase letter and one number)
  - phone: must match a valid phone number format if provided
- Verification of HTTP status codes:
    - 201 Created for successful registrations
    - 400 Bad Request for missing or invalid fields
    - 409 Conflict for duplicate entries (e.g. existing username or email)
- Negative testing:
    - Submissions with missing required fields
    - Invalid data formats or boundary violations
    - Duplicate entries
- Security testing focused on:
    - Input sanitization to prevent injection attacks (such as SQL injection and XSS).
    - Ensuring passwords are encrypted and not returned in any API response.
- Database verification to ensure:
    - User data is correctly persisted.
    - Fields are stored with appropriate formats and timestamps.

### 2.2.2 Out of scope

The following items are explicitly excluded from the scope of this test plan:
- Performance, load, and stress testing of the endpoint.
- Full-scale security penetration testing beyond basic input sanitization
- Compatibility testing with different client applications
- Frontend testing
- Usability or user experience evaluations
- Integration testing with other systems or services beyond the POST /users endpoint.
- Localization or internationalization testing

## 2.3 Project Information
- Product name: User management API 
- Product Version: v1.0 

## 2.4 Schedule and Milestones
To be defined.

## 2.5 Reference material
- API Documentation (Swagger) 
- User Story: US-001 User Registration via API
- Parent US 
- User Schema 
- Security documentation (password encryption) 

## 2.6 Definitions and acronyms 
- API: Application Programming Interface • HTTP: Hypertext Transfer Protocol 
- US: User Story 
- QA: Quality Assurance 
- DB: Database 
- US: User Story

# 3. Testing Strategy
## 3.1 Features to be tested
The following features of the POST /users API endpoint will be tested to ensure correct  functionality, security, and data integrity:

### 3.1.1 User Registration Functionality 
- The API allows successful user registration when valid data is submitted. • The API returns appropriate HTTP status codes: 
    - 201 Created when registration is successful 
    - 400 Bad Request when required fields are missing or data is invalid
    - 409 Conflict when attempting to register with a username or email that  already exists 

### 3.1.2 Field Validations 
- Username 
    - Must be 5–30 characters in length 
    - Can include only letters, numbers, and underscores 
    - Must be unique 
- Email 
    - Must follow a valid email format (e.g. user@example.com) 
    - Must be unique 
- Age 
    - Must be a numeric value between 18 and 60 
- Password 
    - Minimum of 6 characters 
    - Must include at least one uppercase letter and one number 
- Phone (optional) 
    - If provided, must be in a valid international format (e.g. +54965784395) 
### 3.1.3 Security Validations 
- Input sanitization is enforced to prevent common attacks such as SQL injection  and cross-site scripting (XSS). 
- Passwords are encrypted before being stored in the database 
- Passwords are not returned in any part of the API response
- All inputs are validated to avoid injection points 
### 3.1.4 Database Verification 
- All submitted data is correctly stored in the database upon successful  registration 
- Password values are stored as encrypted values 
- A creation timestamp is recorded for each new user 

## 3.2 Features not to be tested
The following features will not be covered in this test plan: 
- GET, PUT/PATCH and DELETE methods (covered by other US) • API authentication 
- Backend and frontend integration 
- Error handling for network connectivity 


## 3.3 Deployment scenarios
Testing for the POST /users endpoint will be conducted in a QA testing environment specifically configured to mirror the production system as closely as possible, while ensuring safety, isolation, and repeatability. Below are the key characteristics of this deployment setup:

- Environment Name: QA testing
- Purpose: Dedicated exclusively to quality assurance activities
- Infrastructure: Matches production setup
- Deployment Source: Latest stable version from the development branch
- Database: Isolated test database designed specifically for this test cycle
- Test Data Management: Clean and controlled test data is inserted at the start of the cycle and fully cleaned up post-execution
- Seeded Users: Includes a minimal set of predefined users to support validation of duplicate and conflict scenarios
- Mocked Services: Third-party dependencies such as email verification are mocked to allow testing in a controlled environment
- Access Control: Secured via VPN using environment-specific credentials; all test accounts and tokens are managed by the QA team and stored securely
- Isolation: Environment is fully isolated from other QA teams and projects, preventing interference from parallel activities
- Production Safety: No live or production data is used at any time
- Performance Testing: Limited load tests may be conducted based on available hardware resources

This configuration ensures that all testing activities reflect real-world behavior of the API while protecting production systems and enabling safe, repeatable validations.

## 3.4 Testing approach
Testing will be performed manually using Postman to execute API requests and analyze  responses. Additionally, Swagger will be used as a reference for API documentation,  and direct database queries will support backend data verification. The testing process will follow a structured approach to ensure both positive and negative scenarios are  validated. 

### 3.4.1 Test Design Techniques

- Functional testing: Verifies that the endpoint behaves according to the defined requirements, particularly validating the "happy path" for successful user registration with valid inputs.

- Positive testing: Verifies that the API handles valid and complete inputs correctly.
  - Examples:
    - Register with all required and valid data.
    - Register using valid optional fields (e.g., `phone` number).
    - Register using minimal but valid data (excluding optional fields).
    - Register with boundary-valid data (e.g., `username` of 5 or 30 characters).

- Equivalence partitioning: Input values are divided into valid and invalid equivalence classes to optimize test coverage.
  - Example: For the `age` field:
    - Valid: 25, 40
    - Invalid: "twenty", 15, 65

- Boundary value analysis: Checks values at the edges of valid ranges to catch small validation errors.
  - Example: For the `username` field:
    - Valid: 5 and 30 characters
    - Invalid: 4 or 31 characters

- Negative testing: Tests API behavior when receiving invalid, incomplete or incorrect input.
  - Examples:
    - Missing required fields
    - Duplicate email
    - Invalid password (e.g., no uppercase letter or number)

- API response validation: Validates the structure and correctness of the API response.
  - Examples:
    - Correct HTTP status codes for each scenario (201, 400, 409)
    - Response body contains only expected fields (e.g., user ID, success message)
    - Sensitive fields (e.g., password, token) are not included in the response payload
    - Error messages are descriptive but do not leak internal system details

- Data integrity testing: Ensures that upon successful user creation:
  - All user data is correctly stored in the database
  - Passwords are encrypted, not stored in plain text
  - A creation timestamp is recorded properly

- Security testing: Attempts to expose or manipulate sensitive data through manual techniques.
  - Examples:
    - Passwords are not present in API responses
    - Inputs are sanitized to prevent injection attacks (e.g., SQL Injection, XSS)
    - Submitting `<script>alert(1)</script>` to verify input sanitization

- Performance testing: Measures how the system behaves under expected and peak conditions.
  - Examples:
    - Test response times for single user registration under normal load
    - Validate registration functionality under concurrent user submissions
    - Monitor latency, throughput, and error rates during peak load
    - Identify bottlenecks (e.g., database latency, encryption overhead)

- Scalability testing: Evaluates the system’s ability to handle increasing amounts of load gracefully.
  - Examples:
    - Push the API beyond expected peak loads to identify breaking points
    - Monitor for crashes, degraded performance, or timeout errors
    - Ensure that the API recovers gracefully after load returns to normal

# 4. Test Environment
## 4.1 Prerequisites 
Before executing the test cases for the `POST /users` API endpoint, the following prerequisites must be met to ensure a stable and testable environment:

- The API must be deployed and accessible at the designated endpoint.
- A working database should be available and configured to support read and write operations.
- Valid database credentials must be provided for database access.
- If the API requires authorization, valid JWT tokens or API keys must be available and included in test requests where applicable.
- Any necessary test data (such as predefined users) should be created before the test execution.
- Database reset or rollback scripts must be available to ensure test isolation and data consistency between runs.
- The QA/testing environment must remain stable and isolated throughout the testing phase.

## 4.2 Operating systems 
The tests will be executed from the tester’s local environment, which is running  Windows 11 Pro. 


## 4.3 Hardware 
- Memory: 12 GB RAM  
- Processor: AMD Ryzen 5 3600 6-Core Processor | 3.95 GHz  
- Hard Disk: 446 GB (SCSI)  
- Network: Stable broadband connection with ≥100 Mbps download/upload speed, sufficient for API interaction and database access.

These specifications are sufficient for executing manual API tests, database verification queries.

## 4.4 Software 
- Application server runtime: Node.js 20  
- Database: PostgreSQL 14  
- Tools: Postman, Swagger, SQL Client  
- Security: Access via VPN, Auth Token (JWT)  
- Operating system: Windows 11 Pro  
- Browser: Chrome

# 5 Risks and Testing Constraints
## 5.1 Risks and Assumptions 

### 5.1.1 Risks


| Risk ID | Risk                                                                 | Mitigation plan                                                                                  | Severity |
|--------|----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|----------|
| 1      | The API structure or behavior might change without notice            | Stay in regular contact with developers and check for updates often.                             | High     |
| 2      | Time constraints may limit full test coverage                        | Focus on the most important features and parts that are more likely to fail.                     | High     |
| 3      | QA might not get access to the API or database, which could delay testing | Request access early in the sprint and confirm it before test execution begins. Raise a flag immediately if access is not granted on time. | High     |
| 4      | The API documentation might be incomplete or outdated                | Double-check the documentation before testing and report any problems ASAP.                      | Medium   |
| 5      | Limited QA knowledge about all possible API responses                | Review the API documentation carefully, ask developers for help, and do exploratory testing.     | Medium   |


### 5.1.2 Assumptions 
The following assumptions are made for the execution of this test plan:

- The API documentation is accurate, complete, and up to date.  
- The POST /users registration endpoint does not require authentication for access.  
- The test environment is stable, isolated from production, and does not contain any sensitive production data.  
- All necessary access credentials (API endpoint, database, tokens if applicable) will be provided before testing begins.  
- The development team is available during the testing to support issue investigation, bug triage or clarification requests.  
- No breaking changes (e.g. changes to request/response structure or validation rules) will be introduced midsprint without prior notice.  
- Test data can be created and cleaned up without impacting other team members or test cases.  
- All third-party services or dependencies required by the endpoint are available and operational in the test environment.

# 5.2 Testing Constraints 
- Testing must be completed during Sprint 1, so it may be necessary to prioritize the most important features and the areas most likely to fail.  
- All tests will be done in the QA environment, which may be slightly different from production.  
- Tests will be manual only, automation is not included in this user story.
# 5.3 Education 
QA Engineers participating in this project must have proficiency in API testing tools, particularly Postman and Swagger.  
Familiarity with RESTful API concepts, HTTP status codes, and basic database querying is also required to effectively execute and verify test cases.

# 6. Sample High-Level Test Cases

## 6.1 Successful registration

| Test case ID | Test case description | Expected result |
|--------------|------------------------|-----------------|
| US001-001 | Verify that a user can be successfully registered with all required, valid and unique information | [API] 1. API returns HTTP 201 Created with success message and user ID. 2. Password is not included in response. [DB] 3. User is inserted with encrypted password. 4. Creation timestamp is recorded. |
| US001-002 | Verify successful registration with valid required and optional (phone) information | [API] 1. API returns HTTP 201 Created with success message and user ID. 2. Password is not included in response. [DB] 3. User is inserted with encrypted password. 4. Creation timestamp is recorded. 5. Phone field stored correctly. |

## 6.2 Missing or invalid required fields

| Test case ID | Test case description | Expected result |
|--------------|------------------------|-----------------|
| US001-003 | Verify registration fails when username is missing | HTTP 400 Bad Request with message: "Username is required" |
| US001-004 | Verify registration fails when email is missing | HTTP 400 Bad Request with message: "Email is required" |
| US001-005 | Verify registration fails when password is missing | HTTP 400 Bad Request with message: "Password is required" |
| US001-006 | Verify registration fails when age is missing | HTTP 400 Bad Request with message: "Age is required" |
| US001-007 | Verify registration fails when age is non-numeric (e.g. "twenty") | HTTP 400 Bad Request with message: "Age must be a number" |
| US001-008 | Verify registration fails when email format is invalid (e.g. "email.com" or "user@domain") | HTTP 400 Bad Request with message: "Invalid email format" |
| US001-009 | Verify registration fails when optional phone is in invalid international format (e.g. "12345", "+123abc") | HTTP 400 Bad Request with message: "Invalid phone number format" |
| US001-010 | Verify registration fails when username contains invalid characters (e.g. spaces, "@") | HTTP 400 Bad Request with message: "Username contains invalid characters" |
| US001-011 | Verify registration fails when password does not meet complexity (e.g. no uppercase, no number, less than 6 chars) | HTTP 400 Bad Request with message: "Password must be at least 6 characters and include one uppercase letter and one number" |
| US001-012 | Verify registration fails when request body is empty | HTTP 400 Bad Request with message: "Missing required fields" |

## 6.3 Boundary and format validation

### 6.3.1 Username length

| Test case ID | Test case description | Expected result |
|--------------|------------------------|-----------------|
| US001-013 | Verify that the API returns 400 when the username has less than 5 valid characters and is unique (e.g. 4 characters) | HTTP 400 Bad Request with message: "Username must be between 5 and 30 characters" |
| US001-014 | Verify API returns 201 when username has exactly 5 valid characters and is unique | [API] HTTP 201 Created; [DB] User record created correctly |
| US001-015 | Verify API returns 201 when username length is between 6 and 29 valid characters and unique | [API] HTTP 201 Created; [DB] User record created correctly |
| US001-016 | Verify API returns 201 when username has exactly 30 valid characters and is unique | [API] HTTP 201 Created; [DB] User record created correctly |
| US001-017 | Verify that the API returns 400 when the username has more than 30 valid characters (e.g. 31 characters) | HTTP 400 Bad Request with message: "Username must be between 5 and 30 characters" |

### 6.3.2 Age validation

| Test case ID | Test case description | Expected result |
|--------------|------------------------|-----------------|
| US001-018 | Verify that the API returns 400 when the age is a positive integer less than 18 (e.g. 17) | HTTP 400 Bad Request with message: "Age must be between 18 and 60" |
| US001-019 | Verify API returns 201 when age is exactly 18 (integer) | [API] HTTP 201 Created; [DB] User record created correctly |
| US001-020 | Verify API returns 201 when age is between 19 and 59 (integer) | [API] HTTP 201 Created; [DB] User record created correctly |
| US001-021 | Verify API returns 201 when age is exactly 60 (integer) | [API] HTTP 201 Created; [DB] User record created correctly |
| US001-022 | Verify that the API returns 400 when the age is an integer greater than 60 (e.g. 61) | HTTP 400 Bad Request with message: "Age must be between 18 and 60" |

### 6.3.3 Email length

| Test case ID | Test case description | Expected result |
|--------------|------------------------|-----------------|
| US001-023 | Verify that the API returns a HTTP Status 400 Bad Request when the email has fewer than 6 valid characters (e.g. "a@b.c") | HTTP 400 Bad Request with message: "Email must be at least 6 characters" |
| US001-024 | Verify API returns 201 Created when email length is exactly 6 characters | [API] HTTP 201 Created; [DB] User record created correctly |
| US001-025 | Verify API returns 201 Created when email length is more than 6 characters | [API] HTTP 201 Created; [DB] User record created correctly |

## 6.4 Duplicate entries

| Test case ID | Test case description | Expected result |
|--------------|------------------------|-----------------|
| US001-026 | Verify that registration fails when the provided username already exists in the system | HTTP 409 Conflict with message: "Username is already in use" |
| US001-027 | Verify that registration fails when the provided email already exists in the system | HTTP 409 Conflict with message: "Email is already in use" |

## 6.5 Security validations

| Test case ID | Test case description | Expected result |
|--------------|------------------------|-----------------|
| US001-028 | Verify that SQL injection attempts (e.g. username = "' OR 1=1 --") are rejected, and no unintended behavior occurs | API returns HTTP 403 Forbidden, request rejected without executing SQL |
| US001-029 | Verify that XSS payloads (e.g. `<script>alert("XSS")</script>`) in inputs are sanitized and not reflected in responses | API returns HTTP 403 Forbidden, request blocked |
| US001-030 | Verify passwords are stored as hashed values in the DB, and cannot be reversed or read in plaintext | DB query confirms password field contains hashed string |
| US001-031 | Verify that the API response does not expose sensitive fields (e.g. password, internal tokens) | Response body does not contain sensitive fields |

## 6.6 Data integrity

| Test case ID | Test case description | Expected result |
|--------------|------------------------|-----------------|
| US001-032 | Verify that a creation timestamp is correctly recorded in the database for each newly registered user | DB record shows valid timestamp field after successful registration |
| US001-033 | Verify that all user-provided data (username, email, age, phone, if included) is accurately saved in the database | DB fields contain the exact submitted data |


