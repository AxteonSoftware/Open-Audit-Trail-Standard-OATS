
---

# 📄 spec/audit-trail-spec.md

```markdown
# Open Audit Trail Standard (OATS) Specification v0.1

## 1. Overview

This document defines the canonical structure for audit trail events in GxP-regulated systems.

---

## 2.  OATS Compliance Checklist

### Full Compliance

- [ ] Unique event ID present
- [ ] Timestamp is recorded
- [ ] User is recorded
- [ ] Operation is recorded
- [ ] Object type is identified
- [ ] Object is identified
- [ ] Field-level changes captured
- [ ] Old valuee recorded
- [ ] New values recorded
- [ ] Reason for change captured
- [ ] Source system recorded



## 3. Field Mapping

### Event ID

eventID, AuditID, Record ID, AuditEntryID, AuditTrailID, logID, id

---

### Timestamp

date, time, timestamp, event timestamp, EventTime, created at, recorded at, logged at

---

### User

user id, operator, performed by, login, full name, modified by, changed by, executed by, user

---

### Operation

operation, action, action type, event, activity, transaction, change type, audit type

---

### Object Type

object type, entity type, record type, item type, module type, category

---

### Object

object name, entity, module, table, parameter, target, subject, resource

---

### Field

property, field name, field, attribute

---

### Old Value

previous value, prior value, old value, before, old

---

### New Value

updated value, current value, new value, after, new

---

### Reason

reason for change, justification, comment, remarks, rationale

---

### Source

location, machine id, workstation, terminal id, station, app

---

