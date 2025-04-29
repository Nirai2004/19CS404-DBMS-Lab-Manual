# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - vignesh R

## Scenario Chosen:
University

## ER Diagram:
![Screenshot 2025-04-29 081718](https://github.com/user-attachments/assets/b99d8fc6-904f-4208-a9ca-d8942afcf7a1)
---

## Entities and Attributes

- **student**
  - `st_ID` (Primary Key)
  - `st_Name`
  - `st_Contact`
  - `st_year`
  - `st_age` *(Optional/Derived)*

- **student_registration**
  - `trans_ID` (Primary Key)
  - `tname`
  - `date`
  - `staff_ID` *(possibly duplicated role references)*

- **courses_offered**
  - `staff_ID1`
  - `staff_ID2`
  - `staff_ID3`

- **staff_department**
  - `staff_ID`
  - `course_line`

- **project**
  - `project_ID` (Primary Key)
  - `name`
  - `date`
  - `staff_ID`

---

## Relationships and Constraints

- **Enroll** (`student` ↔ `student_registration`)
  - **Cardinality**: Many-to-Many
  - **Participation**: Partial (student), Total (student_registration)

- **courses** (`student_registration` ↔ `courses_offered`)
  - **Cardinality**: Many-to-Many

- **staff** (`student_registration` ↔ `staff_department`)
  - **Cardinality**: Many-to-One

- **manages** (`staff_department` ↔ `project`)
  - **Cardinality**: One-to-Many

---

## Extension: Prerequisite / Billing

- **Prerequisite**:
  - Can be modeled via a **recursive relationship** on `courses_offered`
  - Example: `course_ID` → prerequisite `course_ID`

- **Billing**:
  - Add an entity like `billing` with attributes:
    - `bill_ID`, `amount`, `payment_method`, `due_date`
  - Connect it to `student_registration`

---

## Design Choices

- **Entity separation** improves modularity and reflects real-world concepts.
- Multiple `staff_ID`s in `courses_offered` support **team/co-teaching**.
- `project` entity supports **research/project tracking** for staff.
- Dotted attribute `st_age` implies it's **derived** (possibly from DOB).
- Some **role ambiguity** for `staff_ID` in `student_registration` should be clarified.

---

## RESULT

The ER model efficiently captures academic registration, staffing, and project details. Further improvements could include:
- Resolving repeated `staff_ID` usage.
- Clarifying course relationships.
- Explicit modeling of prerequisites and billing features.
