

---

### 1. Introduction

#### 1.1 Purpose of the Document
The Process Design Document outlines the business processes selected for automation using UiPath Robotic Process Automation (RPA) technology. It details the sequence of steps involved in the process, along with conditions and prerequisites necessary for its automation. This document serves as foundational documentation for developers to gather the required details for automating the business process.

#### 1.2 Objectives
The automation of this process is part of a larger project initiative within ACME Systems Inc., specifically in the Finance and Accounting department. The objectives of this automation are:
- Deliver faster processing.
- Reduce the duration of time-consuming activities.
- Leverage automation to enhance the overall performance and reliability of the department.

#### 1.3 Process Key Contacts

| Role          | Name | Date of Action | Notes                               |
|---------------|------|----------------|-------------------------------------|
| Process SME   | TBD  |                | Point of contact for business exceptions and passwords. |
| Reviewer/Owner| TBD  |                | Point of contact for process exceptions and approval for production. |

---

### 2. AS IS Process Description

#### 2.1 Process Overview

**AS IS Process Details:**
- **Process Full Name:** GenerateYearlyReport for Vendor
- **Function:** Reporting
- **Department:** Finance and Accounting
- **Process Short Description:** Download all monthly reports for a specific vendor and generate a yearly report.

**Role Required for Performing the Process:** System 1 User

**Process Schedule:** Yearly, in mid-January

**Number of Items Processed/Month:** 7 – 15 Vendors

**Average Handling Time per Item:** 15 min/Vendor

**Peak Period(s):** None

**Number of FTEs Supporting this Activity:** 1

**Level of Exception Rate:** Between 1 and 3 monthly reports for each vendor could be missing. Those months are to be ignored.

**Input Data:** VendorTaxID

**Output Data:** Yearly Report – Excel File, Upload ID

#### 2.1.1 In Scope for RPA
- Full Scope for RPA - the process is to be 100% automated

#### 2.1.2 Out of Scope for RPA
- There are no activities out of scope for RPA
### 2. AS IS Process Description (Continued)

#### 2.2 Detailed Process Map

**Step** | **Short Description**
--- | ---
1.1 | Open the ACME System 1 web application.
1.2 | Log in to System 1. Required input data: email and password.
1.3 | Access the Dashboard - the central location, where the user can pick a specific menu item.
1.4 | Access the Work Items Listing to view all the available tasks to be performed (Output data: list of tasks).
1.5 | For each activity of the WI4 type, perform the following steps:

1.5.A | Open the Details page of the selected activity to retrieve the Vendor Tax ID (Output data: TaxID).
1.5.B | Go back to the Dashboard and access the Download MonthlyReport section in the Reports menu.
1.5.C | Fill in the Vendor TaxID and download ALL the corresponding monthly reports for 2023.
1.5.D | Group all the downloaded monthly reports into a single Excel yearly report with the “Yearly-Report-2023-TAXID.xlsx” name.
1.5.E | Upload the resulting Excel yearly report in the “Upload Yearly Report” section in the Reports menu.
1.5.F | Fill in the Vendor TaxID, set the year as 2023, and select the file on your hard drive. This will return a unique upload ID.
1.5.G | Go back to the Work Item Details page and select Update Work Item.
1.5.H | Set the status to “Completed”. Add the following comment: "Uploaded with ID uploadID”.
1.6 | Continue with the next WI4 activity.

---

### 2.3 Detailed Process Steps

**Step Action Description** | **Screenshot** | **Expected Result** | **Remarks**
--- | --- | --- | ---
1.1 | Open the ACME System 1 web application. | System 1 WebApp is opened | Possible exception: - Handle exception if Web app not available
1.2 | Log in to System 1. Required input data: email and password. | Access to the dashboard | Possible exception: - Handle exception if Incorrect email or Password
1.3 | Access the Dashboard - the central location where the user can pick a specific menu item. | The display of each item in the menu | 
1.4 | Access the Work Items listing to view all the available tasks to be performed (Output data: list of tasks). | The display of the task list | 
1.5 | For each activity of the WI4 type, perform the following steps: | | Possible exception: Handle exception if no task of type 'Generate Yearly Report for Vendor’ exist


Certainly, here's the continuation:

---

### 2.5 Error Mapping and Handling

**Error Name** | **Step Where Error is Encountered** | **Parameters** | **Action to be Taken**
--- | --- | --- | ---
Application unresponsive/page not loading | Any step | No response/blank page | Retry 2 times. Close application and rerun the sequence if necessary.

### 2.6 In-Scope Application Details

**Application Name & Version** | **System Language** | **Login Module** | **Interface Environment/Access Method** | **Comments**
--- | --- | --- | --- | ---
ACME System 1 | EN | Web | Web Browser | 
Microsoft Excel | EN | n/a | Client | Local desktop

### 3. Development Details

#### 3.1 Prerequisites for Development
- Development or testing environments provided.
- Environments replicate production environment.
- Developers have dedicated system and application access.

#### 3.2 Password Policies
- Users manage their passwords; no special policies.

#### 3.3 Credentials and Asset Management
- Logon details stored under Windows Credential Manager or UiPath Orchestrator Assets.

### 4. Document Approval Flow

**Version** | **Flow** | **Role** | **Organization (Dept.)** | **Signature and Date**
--- | --- | --- | --- | ---
1.0 | Document prepared by | Business Analyst | [Name] [Surname] | [Signature] [Date]
1.0 | Document Approved by | Business Process Owner | [Name] [Surname] | [Signature] [Date]
1.0 | Document Approved by | Dev/RPA Solution Architect | [Name] [Surname] | [Signature] [Date]


---
