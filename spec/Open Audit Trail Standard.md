# Open Audit Trail Standard (OATS) v1.0

## Table of contents

1. Open Audit Trail Standard (OATS)
2. OATS technical details  
3. How other systems (e.g., LIMS, MES) map the defined objects  
4. OATS – How to implement an Audit Trail  
5. History and background
6. About the founder

---

## 1. Open Audit Trail Standard (OATS)

An open, vendor-neutral standard for designing, storing, and analyzing audit trails in GxP-regulated systems.

OATS is intended for software product companies that build solutions for GxP-regulated industries such as pharmaceuticals and life sciences. Its goal is to standardize audit trail fields across different software systems, making audit data easier to interpret, compare, and analyze.

By establishing a common structure and shared definitions, OATS improves cross-system interoperability, enhances clarity around the meaning of each audit field, and supports more efficient compliance, reporting, and investigation activities.

---

## 2. Purpose & scope

### 2.1 Purpose

Audit trails across systems such as LIMS, MES, and QMS are often inconsistent in structure, terminology, and data quality. These differences make regulatory audits, system integration, and centralized analysis significantly more difficult and time-consuming.

The Open Audit Trail Standard (OATS) defines a unified and vendor-neutral approach to designing, storing, and interpreting audit trail data in GxP-regulated environments. Its purpose is to:

- Enable interoperability between different software systems  
- Provide a consistent and predictable audit trail structure  
- Simplify regulatory compliance with FDA and GxP requirements  
- Support centralized, cross-system audit trail analysis  
- Improve clarity and understanding of what each audit field represents  

By establishing a shared standard, OATS reduces ambiguity, improves data quality, and strengthens trust in audit trail information across the entire regulated ecosystem.

---

### 2.2 Scope

OATS applies to software products used in GxP-regulated industries, including but not limited to:

- Laboratory Information Management Systems (LIMS)  
- Manufacturing Execution Systems (MES)  
- Quality Management Systems (QMS)  
- Electronic Batch Records (EBR)  
- Clinical and regulatory systems  
- Any application that generates audit trail data for compliance purposes  

The standard covers:

- Required audit trail fields  
- Field definitions and expected behavior  
- Data types, formats, and naming conventions  

OATS does not prescribe specific technologies, databases, or implementation frameworks. Instead, it provides a flexible and technology-agnostic model that can be adopted by any vendor or development team.

---

## 3. OATS technical details

### OATS recommended fields in your database

The most effective way to standardize an audit trail is to use consistent and unambiguous field names in the database. OATS recommends naming the fields exactly as defined in the standard to ensure clarity, interoperability, and ease of interpretation across different systems.

- [ ] ID  
- [ ] Timestamp  
- [ ] UserID  
- [ ] Operation  
- [ ] ObjectType  
- [ ] Object  
- [ ] Field  
- [ ] OldValue  
- [ ] NewValue  
- [ ] Reason  
- [ ] Source  

Examples 
- examples/gxp-even.json
- Audit Trail Table - Axteon Audit Trail Review.png


---

### ID  
A unique identifier for each audit trail event.  
Ensures every recorded action can be referenced, traced, and retrieved without ambiguity.

### Timestamp  
The exact date and time when the event occurred.  
Used to reconstruct sequences of actions, support investigations, and demonstrate data integrity.

### UserID
The person or system account that performed the action.  
Provides accountability and supports compliance with GxP and FDA expectations for traceability.

The UserID should identify the user who performs an action, so it should be the login name or a combination of the login name with the user’s first and last name. Using only the last name is not a unique identifier, so it is not a good choice.

### Operation  
The type of action performed, such as create, update, delete, approve, or login.  
Helps categorize events and understand the nature of the change.

### ObjectType  
The category or type of entity affected by the action, for example: sample, batch, record, document, or configuration.  
Provides context for what kind of item was changed.

### Object  
The specific item that was modified, usually identified by a name, ID, or unique reference.  
Allows investigators to locate the exact record involved.

### Field  
The specific field or attribute that was changed.  
Used when the operation modifies a single property of an object, such as status, quantity, or owner.

### OldValue  
The value of the field before the change.  
Required for understanding what was modified and for reconstructing historical states.

### NewValue  
The value of the field after the change.  
Shows the result of the action and supports comparison with the previous state.

### Reason  
The justification provided for the change, when required by process or regulation.  
Supports compliance with GxP expectations for intentional, documented changes.

### Source  
The system, module, or interface where the action originated.  
Useful for identifying automated changes, integrations, or external systems contributing audit events.

---

## 4. How other systems map the defined objects

Many systems use different names for the same audit trail fields. While this may not cause technical issues within a single system, it creates significant challenges for those reviewing audit trails. Fields with different names or unclear meanings can lead to confusion, misinterpretation, and ultimately GxP nonconformances.

Consistent terminology is essential to ensure that reviewers, auditors, and investigators clearly understand what each field represents. Without standardization, the risk of incorrect conclusions, missed events, or incomplete investigations increases, directly impacting data integrity and regulatory compliance.

---

### ID  
Common equivalents:  
eventID, AuditID, Record ID, AuditEntryID, AuditTrailID, logID  

---

### Timestamp  
Common equivalents:  
date, time, timestamp, event timestamp, EventTime, created at, recorded at, logged at  

---

### UserID  
Common equivalents:  
user ID, operator, performed by, login, full name, modified by, changed by, executed by  

---

### Operation  
Common equivalents:  
operation, action, action type, event, activity, transaction, change type, audit type  

---

### ObjectType  
Common equivalents:  
object type, entity type, record type, item type, module type, category  

---

### Object  
Common equivalents:  
object name, entity, module, table, parameter, target, subject, resource  

---

### Field  
Common equivalents:  
property, field name, attribute  

---

### OldValue  
Common equivalents:  
previous value, prior value, before  

---

### NewValue  
Common equivalents:  
updated value, current value, after  

---

### Reason  
Common equivalents:  
reason for change, justification, comment, remarks, rationale  

---

### Source  
Common equivalents:  
location, machine ID, workstation, terminal ID, station, application  

---

## 5. OATS – How to implement an Audit Trail

To implement an audit trail using OATS, you need to create audit trail records based on the fields defined in the standard. Before saving a new audit trail entry, it is important to retrieve the latest version of the object from the database and compare it with the updated version you are about to save.

This comparison allows you to identify which fields have changed and record those differences accurately in the audit trail. Only the fields that differ between the old and new versions should generate audit trail entries.

---

## 6. History and background

The Open Audit Trail Standard (OATS) was founded by Adrian Krzesniak following extensive research on audit trail practices conducted in 2026. This research revealed that audit trails across GxP-regulated systems lacked consistency in structure, terminology, and data representation. These inconsistencies created significant challenges for auditors, investigators, and software vendors, often leading to misunderstandings, inefficiencies, and avoidable GxP nonconformances.

Recognizing the need for a unified and vendor-neutral approach, Adrian Krzesniak initiated the development of OATS as an open standard that any software provider could adopt. The goal was to create a common language and structure for audit trail data—one that would improve clarity, interoperability, and regulatory readiness across the entire life sciences ecosystem.

OATS was designed from the beginning to be technology-agnostic, allowing it to be implemented in any system architecture or database model. Its development was informed by real-world system comparisons, regulatory expectations, and feedback from professionals working in pharmaceuticals, biotechnology, and quality management.


## 7. About the founder


Adrian Krześniak combines his expertise in software development, regulatory compliance, and computer system validation to create solutions that address the unique challenges of GxP-regulated industries. With a background in both software development and computer system validation, he has a deep understanding of the complexities involved in maintaining data integrity, ensuring compliance, and supporting efficient operations in regulated environments.

More information about the founder can be found on his professional profile:  
https://www.linkedin.com/in/adriankrzesniak/

Adrian is a well-known computer system validation trainer, with courses on Udemy covering topics such as:

- Validation and Maintenance of Computerized Systems
- Computer System Assurance – Quality Assurance of Computerized Systems
- Agile Validation in GxP
- Data Integrity for Computerized Systems in GxP
- Validation of Mobile Applications
- Spreadsheet Validation Based on GAMP 5
- Validation of AI & ML GxP Systems
- Auditing GxP Computer Systems for Regulatory Compliance

https://axteon.com/computer-system-validation/Books

Adrian has also written several books, published on Udemy as books and eBooks:

- Software Development for GxP-Regulated Industries: Delivering GxP-Compliant Software in an Agile Way
- Data Integrity in Computerized Systems: Data Integrity and GxP
- Digital Validation: Digital Transformation of Computer System Validation and Maintenance Processes
- Software Development Manager Guide: People, Process, Tools, Delivery

https://axteon.com/computer-system-validation/Training

