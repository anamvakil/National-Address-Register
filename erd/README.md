## Entity Relationship Diagrams (ERD)
# Entity Relationship Diagram (ERD)  
## National Address Register (GA5)

This Entity Relationship Diagram (ERD) represents the normalized relational database design for the **National Address Register (GA5)** project.  
The schema follows **Third Normal Form (3NF)** principles to minimize redundancy, enforce data integrity, and support scalable querying.

---

## Design Overview

The database follows a hub-and-spoke design in which a central address table is connected to multiple reference tables representing geographic and mailing dimensions.

- Central entity: `GA5_AddressNormalized`
- Supporting dimension tables: Street, Municipality, Province, Geography, Mailing Address
- Relationships are enforced using primary and foreign key constraints

---
<img width="1321" height="774" alt="image" src="https://github.com/user-attachments/assets/f795a225-05dd-457f-ba02-fb32ff8a40cf" />
---

## Entities and Purpose

### `GA5_AddressNormalized` (Central Table)
Stores the core address information and serves as the primary entity in the schema.

Key attributes include:
- Unique address identifiers (`AddressID`, `LOC_GUID`, `ADDR_GUID`)
- Civic information (`CIVIC_NO`, `CIVIC_NO_SUFFIX`, `APT_NO_LABEL`)
- Foreign keys linking to normalized reference tables
- Business usage attributes (`BU_N_CIVIC_ADD`, `BU_USE`)

---

### `GA5_Street`
Contains standardized street-level information.

- Reduces duplication of street names and types
- Supports consistent street referencing across all addresses

---

### `GA5_Municipality`
Stores census subdivision (CSD) information.

- Supports bilingual naming (English and French)
- Includes municipality classification codes
- Enables regional and administrative analysis

---

### `GA5_Province`
Stores province-level reference data.

- Provides standardized province codes
- Supports province-level aggregation and filtering

---

### `GA5_Geography`
Stores geographic and spatial reference attributes.

- Includes dissemination block identifiers
- Contains coordinate attributes (X, Y)
- Linked optionally depending on data availability

---

### `GA5_MailingAddress`
Stores mailing-specific address information.

- Separated from civic addresses to avoid redundancy
- Supports optional linkage for addresses with different mailing details

---

## Relationship Design

- All relationships are one-to-many from reference tables to `GA5_AddressNormalized`
- Optional foreign keys are used where complete data may not be available
- Referential integrity is enforced using foreign key constraints

---

## Normalization Strategy

- Data normalized up to Third Normal Form (3NF)
- Repeating and descriptive attributes moved to lookup tables
- Reduces update, insertion, and deletion anomalies
- Improves data consistency and maintainability

---

## Tools Used

- ERD created using Mermaid and ER diagramming tools
- Schema implemented using T-SQL in SQL Server

---

## Related Components

- SQL Scripts: See `/sql/` directory
- Project Report: See `/report/GA5_Project.pdf`

---

## Contribution Note

This was a group academic project.  
My primary contributions included:
- Designing the normalized database schema
- Defining table relationships and constraints
- Creating the ERD and validating normalization logic
- Supporting schema implementation in T-SQL

---

This ERD serves as the structural blueprint for database implementation and analytical querying.

