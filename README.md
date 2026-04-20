# HR Attrition Dashboard with Row Level Security (RLS)

## 📌 Overview
This project demonstrates enterprise-level Power BI development including:

- Star schema modelling
- DAX measures
- Row Level Security (RLS)
- Executive summary reporting
- Power BI Service governance

Dataset: IBM HR Analytics Attrition Dataset (Kaggle)

---

## 📂 Data Model

### Tables
- **DimEmployee** – employee attributes  
- **DimDepartment** – unique department list  
- **DimManager** – manager details + email  
- **FactAttrition** – attrition facts  
- **Summary tables** – aggregated views for Executive RLS  

### Relationships
- `DimEmployee[EmployeeID]` → `FactAttrition[EmployeeID]` (1:*)  
This is the core relationship driving the model.

---

## 🧮 DAX Measures
- Attrition Count  
- Headcount  
- Attrition Rate  
- Avg Monthly Income  
- Attrition by Department  
- Attrition by Manager  

(Full DAX code included in `/Measures`)

---

## 🔐 Row Level Security (RLS)

### HR Role
- Full access  
- No filters applied  

### Manager Role
Managers see only their team  
Filter:  
`DimManager[ManagerEmail] = USERPRINCIPALNAME()`

### Executive Role
Executives see summary only  
Filter:  
`FALSE()` on DimEmployee  
Uses summary tables for aggregated reporting.

---

## 📊 Report Pages
- Workforce Attrition Dashboard (Managers/Directors)
- Executive Summary (Executives only)

---

## ☁️ Power BI Service
- Published to workspace  
- RLS roles created  
- Users assigned  
- Tested using "View As"  
- Added to App for distribution  

---

## 📸 Screenshots
Include:
- Data model  
- RLS role setup  
- View As (HR, Manager, Executive)  
- Executive Summary page  
- Manager/Director page  

---

## 📁 Repository Structure
