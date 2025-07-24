Test plan: Quickshop Mobile App

# Table of Contents

1. [Document Information](#1-document-information)  
 1.1 [Author](#11-author)  
 1.2 [Revision history](#12-revision-history)  
 1.3 [Approval process and reviewers](#13-approval-process-and-reviewers)  

2. [Introduction](#2-introduction)  
 2.1 [Overview](#21-overview)  
 2.2 [Scope](#22-scope)  
  - [In Scope](#in-scope)  
  - [Out of Scope](#out-of-scope)  
 2.3 [Project information](#23-project-information)  
 2.4 [Schedule and milestones](#24-schedule-and-milestones)  
 2.5 [Reference material](#25-reference-material)  
 2.6 [Definitions and acronyms](#26-definitions-and-acronyms)  

3. [Testing strategy](#3-testing-strategy)  
 3.1 [Features to be tested](#31-features-to-be-tested)  
  3.1.1 [User registration and login](#311-user-registration-and-login)  
  3.1.2 [Product browsing and search](#312-product-browsing-and-search)  
  3.1.3 [Cart management and purchases](#313-cart-management-and-purchases)  
  3.1.4 [GPS store locator](#314-gps-store-locator)  
  3.1.5 [Push notifications](#315-push-notifications)  
  3.1.6 [Usability metrics](#316-usability-metrics)  
  3.1.7 [Compatibility](#317-compatibility)  
  3.1.8 [Performance metrics](#318-performance-metrics)  
  3.1.9 [Security validations](#319-security-validations)  
  3.1.10 [Localization checks](#3110-localization-checks)  
  3.1.11 [Offline behavior](#3111-offline-behavior)  
 3.2 [Features not to be tested](#32-features-not-to-be-tested)  
 3.3 [Deployment scenarios](#33-deployment-scenarios)  
 3.4 [Testing approach](#34-testing-approach)  
  3.4.1 [Test design techniques](#341-test-design-techniques)  

4. [Test environment](#4-test-environment)  
 4.1 [Prerequisites](#41-prerequisites)  
 4.2 [Operating systems](#42-operating-systems)  
 4.3 [Hardware](#43-hardware)  
 4.4 [Software](#44-software)  

5. [Risks and testing constraints](#5-risks-and-testing-constraints)  
 5.1 [Risks and assumptions](#51-risks-and-assumptions)  
  5.1.1 [Risks](#511-risks)  
  5.1.2 [Assumptions](#512-assumptions)  
 5.2 [Testing constraints](#52-testing-constraints)  
 5.3 [Education](#53-education)  

6. [Sample high-level test cases](#6-sample-high-level-test-cases)

# 1. Document Information

## 1.1 Author
| Author             | Email                       | Date       |  
|--------------------|-----------------------------|------------|
| Rosa Micaela Serra | serra.rosamicaela@gmail.com | 05-06-2025 |

## 1.2 Revision history
| Author             | Date       | Version | Description                              |
|--------------------|------------|---------|------------------------------------------|
| Rosa Micaela Serra | 05-06-2025 | 1.0    | Initial version                          |


## 1.3 Approval process and reviewers
The document will be reviewed by the QA team and PO. Final approval will be granted based on consensus during scheduled review sessions.

# 2. Introduction

## 2.1. Overview

This test plan outlines the testing strategy for the QuickShop Android Mobile Application, an online marketplace that enables users to register, browse and search for products, add items to a shopping cart, make purchases, locate nearby stores using GPS, and receive push notifications, among other functionalities. The objective is to ensure the app delivers high quality, stability, usability, and compatibility across different Android devices and environments.

To achieve this, the following types of testing will be conducted, each focusing on different aspects of the application’s performance and behavior:

- Functional testing, to verify that all core features work correctly and as expected  
- Usability testing, to ensure that users can intuitively navigate and interact with the app's core features  
- Compatibility testing, to validate that the app operates smoothly across a variety of Android devices and OS versions  
- Interrupt testing, to test how the app responds when interrupted by external events such as incoming calls  
- Performance testing, to assess how efficiently the app handles operations such as loading product lists  
- Security testing, to test secure data handling and access controls  
- Localization testing, to verify the correct rendering of all UI elements (text, numbers, currency, dates) and translations in supported languages or regional settings  
- Offline testing, to confirm that the app handles connectivity loss gracefully  

## 2.2. Scope

### In Scope

This test plan focuses on validating the functionality, performance, compatibility, usability, and security of the QuickShop Android Mobile Application from the shopper perspective. The following items are considered in scope:

- Functional testing of the core buyer features:  
  - Register and log in  
  - Browse and search products  
  - Add items to the cart  
  - Make purchases  
  - Use GPS to locate physical stores  
  - Receive push notifications  

- Usability testing, specifically measuring:  
  - Time required to complete key tasks (e.g. product search)  
  - Clarity of navigation and screen layout on phones and tablets  
  - Accessibility aspects like text readability, touch area sizes, and user guidance  

- Compatibility testing across Android 13+ devices, including:  
  - Phones:  
    - Xiaomi Redmi 14C  
    - Motorola Edge 40 Neo  
    - Samsung Galaxy A26  
  - Tablets:  
    - HUAWEI MatePad 11.5"S  
    - Motorola Pad 60 Pro  
    - Samsung Galaxy Tab A9  

- Interrupt testing of the app’s stability during:  
  - Incoming calls or SMS  
  - Notifications during app use (especially during checkout or GPS operations)  
  - Alarm ringing while the app is in use  
  - Switching between apps or locking/unlocking the device  

- Performance testing focused on:  
  - Network performance (e.g. response times during product browsing and purchase)  
  - Battery usage during active sessions  
  - Memory usage  

- Security testing, including:  
  - Validation of encrypted password handling and secure session management  
  - Ensuring no sensitive data is stored in plain text or cached locally  

- Localization testing validating:  
  - Correct rendering of text, currency, and datetime formats for supported countries (e.g. Argentina)  

- Offline testing verifying app behavior during connection loss, including:  
  - Display of cached products previously browsed  
  - Display of appropriate error messages when actions cannot be completed offline  

### Out of Scope

The following features and aspects are excluded from this testing effort:

- Seller interface  
- Review and ratings functionality  
- Favorites/wishlist functionality  
- Purchase history section  
- Customer support features  
- Non-Android platforms (iOS and other mobile platforms are excluded)  
- Advanced security testing  

## 2.3. Project information

- Product name: QuickShop  
- Product version: v1.0  

## 2.4. Schedule and milestones

- Sprint 1: July 7 – 14, 2025  

## 2.5. Reference material

- QuickShop Feature Spec Document  
- Figma design mockups  
- BrowserStack documentation  

## 2.6. Definitions and acronyms

- QA: Quality Assurance  
- OS: Operating system  

# 3. Testing strategy

## 3.1. Features to be tested

The following features and behaviors of the QuickShop App will be tested to ensure functional behaviour, usability, security, and platform stability:

### 3.1.1 User registration and login

- Users can register with valid email and password credentials  
- System prevents duplicate accounts using the same email  
- Passwords are validated for minimum complexity requirements  
- Session tokens are securely stored and expire appropriately  

### 3.1.2 Product browsing and search

- Users can search for products using keywords or categories  
- Product results load correctly and match the search  
- Product details view displays accurate information  

### 3.1.3 Cart management and purchases

- Users can add, remove, and update quantities of items in the cart  
- Cart totals and price calculations are accurate  
- Users can proceed through a multi-step checkout process  
- Purchase is confirmed with appropriate UI feedback and order ID  

### 3.1.4 GPS store locator

- GPS permissions are requested on first use  
- App can retrieve and display nearby store locations on a map  
- Results update based on user’s current or selected location  

### 3.1.5 Push notifications

- Device registration for push notifications is successful  
- App receives and displays order updates or promotional messages  

### 3.1.6 Usability metrics

- Time to complete a full purchase flow is under 3 minutes  
- Button labels and touch targets are accessible and visible on all devices  
- Layout remains consistent across screen sizes and orientations  

### 3.1.7 Compatibility

- App installs and runs correctly on the following Android 13+ devices:  
  - Phones: Xiaomi Redmi 14C, Motorola Edge 40 Neo, Samsung Galaxy A26  
  - Tablets: HUAWEI MatePad 11.5"S, Motorola Pad 60 Pro, Samsung Galaxy Tab A9  

### 3.1.8 Performance metrics

- Product list loads in under 2 seconds over Wi-Fi and under 5 seconds over 4G  
- Battery drain does not exceed 2% over a 15-minute session  

### 3.1.9 Security validations

- Passwords are never stored in plain text  
- App prevents access to secure features without valid authentication  
- No sensitive information remains in app cache or logs after logout  

### 3.1.10 Localization checks

- Spanish translations are accurate and context-appropriate  
- Currency (Argentinian pounds) and dates follow local formatting rules  
- No text is cut off or misaligned due to translation length  

### 3.1.11 Offline behavior

- When offline, previously visited product data is still accessible  
- Users are warned when actions like checkout require connectivity  
- App syncs cart changes after reconnection without data loss  

## 3.2. Features not to be tested

The following features will not be covered in this test plan:

- Seller interface  
- Review and ratings  
- Favorites/wishlist  
- Purchase history  
- Customer support  
- iOS and other platforms  

## 3.3. Deployment scenarios

- Phones:  
  - Xiaomi Redmi 14C  
  - Motorola Edge 40 Neo  
  - Samsung Galaxy A26  
- Tablets:  
  - HUAWEI MatePad 11.5"S  
  - Motorola Pad 60 Pro  
  - Samsung Galaxy Tab A9  
- Emulator: Android Studio  
- BrowserStack  
- Internet connection is required for the testing  

## 3.4. Testing approach

Testing will be conducted manually on physical Android devices and through emulators in Android Studio. For cross-device and cross-version testing, BrowserStack will be used when available. All tests will be guided by defined user stories, acceptance criteria, and exploratory heuristics to ensure full coverage of key scenarios.

### 3.4.1 Test design techniques

- Functional testing:  
  - Verifies that all features work according to specifications  
  - Focus is on validating the happy path for tasks like:  
    - User login with valid credentials  
    - Adding a product to the cart  
    - Successfully checking out and receiving confirmation  

- Equivalence partitioning:  
  - Input values (e.g. email, quantity, search terms) are divided into valid and invalid categories to reduce the number of test cases while maintaining coverage  

- Boundary value analysis:  
  - Checks values at the edges of allowed input ranges to uncover off-by-one or validation errors  

- Negative testing:  
  - Validates app behavior when receiving unexpected or invalid input or usage patterns  

- Security testing:  
  - Includes testing for secure login, data encryption, and secure communication  

- Usability testing:  
  - Evaluates how easily a user can navigate and complete tasks  
  - Based on task completion time, clarity of actions, and UI consistency  

- Compatibility testing:  
  - Verifies proper display and functionality across target Android devices and OS versions (Android 13+)  

- Interrupt testing:  
  - Checks how well the app keeps working when something interrupts it  

- Performance testing:  
  - Manual observation of app responsiveness and resource usage  

- Localization testing:  
  - Ensures accurate and culturally appropriate text formatting and translations  

- Offline testing:  
  - Tests how the app behaves when internet connectivity is lost and then restored  

# 4. Test environment

This section outlines the required environment, tools, and configurations used during the mobile testing process. It includes prerequisites, supported operating systems, target hardware, and software tools necessary for executing and managing the tests effectively.

## 4.1. Prerequisites

Before initiating testing activities, the following prerequisites must be met:

- APK built for Android 13 or higher: the application must be compiled and signed for installation on both physical and virtual devices running Android 13 and above  
- Test user accounts: pre-configured test accounts are needed  
- BrowserStack license: a valid license is required to access the cloud-based device lab for cross-device and cross-version testing  
- Test data: dummy products, payment methods, user profiles, and order histories should be available for consistent and repeatable testing  

## 4.2. Operating systems

- Testing will be focused on Android devices running Android 13 or higher  
- Testing using Android Studio and BrowserStack will be carried out on Windows 11  

## 4.3. Hardware

Compatibility testing will be conducted using a set of Android devices running Android 13 or higher.

Phones:

- Xiaomi Redmi 14C  
- Motorola Edge 40 Neo  
- Samsung Galaxy A26  

Tablets:

- HUAWEI MatePad 11.5"S  
- Motorola Pad 60 Pro  
- Samsung Galaxy Tab A9  

All listed devices will be used for manual functional and compatibility testing to validate app behavior, UI rendering, and performance across different resolutions and device configurations. Devices will be either physical or accessed via BrowserStack, depending on availability and test scope. Additionally, hardware features that cannot be tested on BrowserStack and Android Studio, such as the camera, battery consumption or sensors, will be tested on physical devices.

## 4.4. Software

The testing process will leverage the following software tools and platforms:

- Android Studio: used for installing and debugging the app, monitoring logs, and running emulators when needed  
- BrowserStack: enables real-time testing on various Android devices hosted in the cloud  
- Postman: utilized for testing API endpoints and validating backend data flows  
- Jira/TestRail: for managing test cases, documenting bugs, and tracking test execution progress  
- Vysor / Scrcpy (optional): for screen mirroring during remote sessions, demos, or screen recordings  

All tools must be set up to support Android testing and allow collaboration across the QA team.  

# 5. Risks and testing constraints

## 5.1. Risks and assumptions

### 5.1.2. Risks

| Risk                                      | Mitigation plan                                                        | Severity |
|-------------------------------------------|------------------------------------------------------------------------|----------|
| BrowserStack license delay                | Request license early, confirm access before testing                   | High     |
| Android Studio misconfiguration           | Use standardized setup guides and verify SDK/emulator versions         | High     |
| Physical device malfunction               | Maintain backup units and chargers; test in rotation                   | High     |
| QA unfamiliarity with tools               | Provide quick reference guides and internal walkthroughs               | High     |
| GPS draining battery during tests         | Limit long GPS sessions                                                | Medium   |
| BrowserStack device unavailability        | Pre-book test slots                                                    | Medium   |
| Inconsistent emulator behavior            | Prefer physical devices for critical flows                             | Medium   |

### 5.1.2. Assumptions

The following assumptions are made for the execution of this test plan:  
• Test devices are clean or factory reset  
• Selected devices are available on BrowserStack  
• Test user credentials are active and valid  
• Stable internet connection is available  
• Test automation team is available  

## 5.2. Testing constraints

• iOS platform excluded  
• Limited device diversity  
• Time-constrained exploratory testing  

## 5.3. Education

QA team members are expected to have the following knowledge:  
• Basic Android usage and device handling  
• APK installation and log capture  
• BrowserStack usage for remote device testing  
• Manual test case execution and bug reporting  
• Understanding of mobile UI behavior and responsiveness  
• Familiarity with tools like Postman and Jira

# 6. Sample high-level test cases

| TC Id   | Test case description                                         | Expected result                                              | Testing type  | Priority |
|---------|---------------------------------------------------------------|--------------------------------------------------------------|----------------|----------|
| TC001   | Verify that a user can register with valid credentials        | Account is created and user is logged in                     | Functional     | High     |
| TC002   | Verify that a user cannot register with an already used email | Error message is displayed: “Email already in use”           | Functional     | High     |
| TC003   | Verify that a product can be added to the cart                | Product appears in cart with correct details                 | Functional     | High     |
| TC004   | Verify that checkout can be completed with valid data         | Confirmation message and order ID are displayed             | Functional     | High     |
| TC005   | Verify that the GPS store locator displays nearby stores      | Map with accurate nearby store locations is shown            | Functional     | Medium   |
| TC006   | Verify that buttons (e.g. Add to Cart, Checkout) are visible  | All buttons are readable, tappable, and consistently placed  | Usability      | High     |
| TC007   | Verify that the full purchase flow can be completed in <3 min | Timer logs < 3 minutes from login to confirmation            | Usability      | High     |
| TC008   | Verify that product pages are readable on tablets             | UI is not stretched, cropped, or overlapping                 | Usability      | High     |
| TC009   | Verify app installs and launches on Xiaomi Redmi 14C          | App opens without crash or errors                            | Compatibility  | High     |
| TC010   | Verify app installs and launches on Huawei MatePad 11.5"S     | App opens without crash or errors                            | Compatibility  | High     |
| TC011   | Verify app installs and launches on Samsung Galaxy A26        | App opens without crash or errors                            | Compatibility  | High     |
| TC012   | Verify app maintains session after a phone call               | App resumes in same state after call ends                    | Interrupt      | High     |
| TC013   | Verify app maintains session after an alarm                   | App resumes in the same state after the alarm goes off       | Interrupt      | High     |
| TC014   | Verify cart state is preserved after backgrounding the app    | Items remain in cart when returning to app                   | Interrupt      | High     |
| TC015   | Verify product list loads in <2s over Wi-Fi                   | Product list fully visible within 2 seconds                  | Performance    | High     |
| TC016   | Verify battery drain after 15 mins of browsing is <8%         | Device battery usage remains within expected range           | Performance    | Medium   |
| TC017   | Verify that password fields do not display characters         | Input is masked with dots or asterisks                       | Security       | High     |
| TC018   | Verify that all API calls use HTTPS                           | Network inspector shows only HTTPS traffic                   | Security       | High     |
| TC019   | Verify app displays currency in ARS for Argentina             | All prices use "$" and proper formatting                     | Localization   | Medium   |
| TC020   | Verify that Spanish translations appear correctly             | All labels, buttons, and messages are properly translated    | Localization   | Medium   |
| TC021   | Verify cart actions performed offline sync after reconnecting | Items added offline appear correctly after reconnecting      | Offline        | High     |