<h1 align="center">Import Data using Transform Maps</h1>

<p align="center">
  <strong>ServiceNow Data Import & Transformation Workflow</strong>
</p>

<p align="center">
  Automating employee data migration from Excel spreadsheets into ServiceNow using Import Sets, Transform Maps, and Coalesce.
</p>

<p align="center">
  <code>ServiceNow</code>
  <code>Import Sets</code>
  <code>Transform Maps</code>
  <code>Coalesce</code>
  <code>Excel</code>
</p>

## Overview

**Import Data using Transform Maps** is a ServiceNow-based data management project designed to automate the bulk import of employee records from external Excel spreadsheets.

The solution uses **Import Sets** and **Transform Maps** to map, validate, and migrate employee data into a custom target table while using **Coalesce** to prevent duplicate records.

---

## System Flow

```mermaid
flowchart LR
    A[Excel Spreadsheet] --> B[Load Data]
    B --> C[Import Set<br/>Staging Table]
    C --> D[Transform Map]
    D --> E{Employee ID<br/>Coalesce}
    E -->|New Record| F[Insert]
    E -->|Existing Record| G[Update]
    F --> H[Target Table]
    G --> H
    H --> I[Reports & Dashboard]
```

---

## Objectives

<div align="center">

|     | Objective            | Purpose                                  |
| :-: | -------------------- | ---------------------------------------- |
|  01 | Bulk Data Import     | Automate employee data entry from Excel  |
|  02 | Error Reduction      | Reduce manual data entry errors          |
|  03 | Field Mapping        | Map external fields accurately           |
|  04 | Duplicate Prevention | Prevent duplicate records using Coalesce |
|  05 | Data Visualization   | Monitor employee data through dashboards |

</div>

---

## Architecture

```text
                         EXTERNAL SOURCE
                              │
                              ▼
                    ┌───────────────────┐
                    │  Excel Spreadsheet │
                    │       (.xlsx)      │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │    Import Set     │
                    │ u_employee_import │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │   Transform Map   │
                    │   Field Mapping   │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │     Coalesce      │
                    │   Employee ID     │
                    └─────────┬─────────┘
                         ┌────┴────┐
                         ▼         ▼
                      INSERT     UPDATE
                         │         │
                         └────┬────┘
                              ▼
                    ┌───────────────────┐
                    │   Target Table    │
                    │   u_employee_test │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │ Employee Analytics│
                    │     Dashboard     │
                    └───────────────────┘
```

---

## Key Features

### Data Migration

Bulk employee records can be imported from an external `.xlsx` spreadsheet into ServiceNow without manual record-by-record entry.

### Transform Map

The Transform Map handles the mapping between the staging table and the custom target table.

```text
External Excel Field
        │
        ▼
Import Set Field
        │
        ▼
Transform Map
        │
        ▼
Target Table Field
```

### Coalesce-Based Duplicate Prevention

The **Employee ID** field is configured as the unique identifier.

| Import Condition                | ServiceNow Action      |
| ------------------------------- | ---------------------- |
| Employee ID does not exist      | Insert New Record      |
| Employee ID already exists      | Update Existing Record |
| Same Employee ID imported again | Prevent Duplicate      |

### Analytics Dashboard

The imported employee data is visualized through an **Employee Analytics Dashboard** containing:

```text
Department
    └── Pie Chart

Location
    └── Bar Chart

Employee Records
    └── List Report
```

---

## Data Architecture

| Layer      | Component           | Purpose                          |
| ---------- | ------------------- | -------------------------------- |
| Source     | Excel `.xlsx`       | External employee dataset        |
| Staging    | `u_employee_import` | Temporary imported data          |
| Processing | Transform Map       | Field mapping and transformation |
| Validation | Coalesce            | Duplicate detection              |
| Target     | `u_employee_test`   | Final employee records           |
| Analytics  | Reports & Dashboard | Data visualization               |

---

## Technology Stack

<p align="center">

| Platform                    | Tools            | Data             | Analytics  |
| --------------------------- | ---------------- | ---------------- | ---------- |
| ServiceNow                  | Import Sets      | Microsoft Excel  | Reports    |
| Personal Developer Instance | Transform Maps   | `.xlsx`          | Dashboards |
| Custom Tables               | Tables & Columns | Employee Records | Charts     |

</p>

---

## End-to-End Demonstration

```text
01  Create Target Table
        ↓
02  Create Import Set Staging Table
        ↓
03  Prepare Employee Excel Dataset
        ↓
04  Load Data into ServiceNow
        ↓
05  Configure Transform Map
        ↓
06  Auto-Mapping of Fields
        ↓
07  Configure Employee ID as Coalesce
        ↓
08  Run Transformation
        ↓
09  Verify Inserted Records
        ↓
10  Re-import Updated Dataset
        ↓
11  Verify Update vs Insert
        ↓
12  View Employee Analytics Dashboard
```

---

## Project Evidence

The repository contains phase-wise documentation, source files, and screenshots covering:

* Data preparation
* Import Set configuration
* Transform Map configuration
* Field mapping
* Transformation execution
* Coalesce validation
* Transformation history
* Target table records
* Employee Analytics Dashboard

---

## Expected Outcome

```text
Excel Data
    │
    ▼
Automated Import
    │
    ▼
Validated Transformation
    │
    ▼
Duplicate-Free Employee Records
    │
    ▼
Centralized Analytics Dashboard
```

The implementation minimizes manual HR/IT data entry, maintains data integrity, prevents duplicate records, and provides centralized visibility into employee distribution across departments and locations.

---

## Conclusion

This project demonstrates the practical use of **ServiceNow Import Sets and Transform Maps** for enterprise data management.

It provides an automated workflow for importing employee data, mapping external fields, validating records, preventing duplicates through Coalesce, and visualizing the resulting data through ServiceNow Reports and Dashboards.

---

<p align="center">
  <strong>ServiceNow · Import Sets · Transform Maps · Coalesce · Reports · Dashboards</strong>
</p>
