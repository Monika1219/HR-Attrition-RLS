# HR Attrition Dashboard with Row-Level Security (RLS)

## Overview
This project demonstrates enterprise-level Power BI development including:

- Star schema modelling  
- DAX measures  
- Row-Level Security (RLS)  
- Executive summary reporting  
- Power BI Service governance  

Dataset: IBM HR Analytics Attrition Dataset (Kaggle)

---

## Data Model

### Tables
- DimEmployee - employee attributes  
- DimDepartment - unique department list  
- DimManager - manager details + email  
- FactAttrition - attrition facts  
- Summary tables - aggregated views for Executive RLS  

### Relationships
- DimEmployee[EmployeeID] ? FactAttrition[EmployeeID] (1:*)  
This is the core relationship driving the model.

---

## DAX Measures
- Attrition Count  
- Headcount  
- Attrition Rate  
- Avg Monthly Income  
- Attrition by Department  
- Attrition by Manager  

(Full DAX code included in /Measures)

---

## Row-Level Security (RLS)

### Role Definitions in Power BI Desktop
Three RLS roles were created to simulate real organisational access levels:

- **HR Role**  
  Full access, no filters applied.

- **Manager Role**  
  Managers see only their own team.  
  Filter:  
  DimManager[ManagerEmail] = USERPRINCIPALNAME()

- **Executive Role**  
  Executives see only aggregated data.  
  Filter:  
  FALSE() on DimEmployee  
  Summary tables provide the required aggregated reporting.

### RLS Testing in Desktop
Fake manager emails were added to the DimManager table to simulate different management groups.  
These were used for testing via:  
**Modeling ? View as ? Other user**

This allowed validation of RLS behaviour without needing real accounts.

### Deployment to Power BI Service
Power BI Service only accepts **real tenant users** for RLS assignment.  
Fake manager emails cannot be added because they do not exist in the Microsoft tenant.

To validate RLS in the cloud:
- My real account was assigned to the **Manager** role.  
- RLS was tested using **View as** in the Service.  
- Behaviour matched the Desktop RLS logic.

### Summary
- Fake emails were used for Desktop testing only.  
- Real user assignment was used in the Service to demonstrate RLS functionality.  
- This setup accurately reflects real-world RLS implementation while remaining suitable for a portfolio project.

---

## Report Pages
- Workforce Attrition Dashboard (Managers/Directors)  
- Executive Summary (Executives only)

---

## Power BI Service
- Published to workspace  
- Added to App for distribution  

---

## Screenshots
Include:
- Executive Summary page  
- Manager/Director page  
