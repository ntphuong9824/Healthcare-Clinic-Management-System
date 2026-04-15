# Project Memory

⚠️ **Update this file manually as project progresses.** This tracks the current state of the HCMS project for quick reference.

---

## Current Project State

**Status**: Early pre-implementation phase
- Business requirements defined (v0.2 MVP scope)
- Documentation structure established
- **No source code yet** in `Developments/`
- **No test files yet** in `Testing/`

**Last Updated**: 2025-04-15

---

## Immediate Next Steps

1. **Architecture detailed design** in `Document/03_Design/01_Architecture/`
   - System context diagram
   - Component architecture
   - API design (if separate backend)

2. **Database schema** in `Document/03_Design/02_Database_Design/`
   - ERD showing all 5 entities and relationships
   - Migration strategy
   - Sample data for testing

3. **UI/UX mockups** in `Document/03_Design/03_UIUX/`
   - Booking portal (parent view)
   - Receptionist dashboard
   - Physician EMR view
   - Checkout flow

4. **Detailed use cases** in `Document/02_Requirements/Use Cases/`
   - Break down each of the 3 business goals into user stories
   - Acceptance criteria for each feature
   - Non-functional requirements (performance, security)

5. **Implementation planning** in `Document/04_Project_Management/Plans/`
   - Tech stack decision
   - Sprint planning (2-week sprints recommended)
   - Milestone timeline

---

## Tech Stack Status

**Status**: Not yet determined

Options under consideration:
- Frontend: Next.js / React / TypeScript
- Backend: Next.js API routes (full-stack)
- Database: PostgreSQL + Prisma ORM
- Testing: Jest + Playwright

Decision pending: Architecture review meeting.

---

## 5-Entity Data Model (Reference)

```
PATIENT
├── name
├── date_of_birth
├── parent_contact_phone
└── basic_medical_history

APPOINTMENT
├── date_time_slot
├── assigned_physician
├── status (Pending|Confirmed|Completed|Cancelled)
└── patient_id (FK)

VISIT
├── symptoms
├── diagnosis
├── clinical_notes
├── appointment_id (FK)
└── patient_id (FK)

PRESCRIPTION
├── medicine_name
├── dosage_instruction
├── duration_days
├── visit_id (FK)

BILLING
├── consultation_fee
├── total_amount
├── payment_status (Paid|Unpaid)
├── visit_id (FK)
└── patient_id (FK)
```

---

## Constraints Reminders

- **5-entity boundary is sacred** - Do not add tables without v2.0 spec
- **Cash-only billing** - No insurance integration ever
- **Max 2 doctors** - Scale for small practice only
- **Parent-first UX** - Booking must be 3-clicks or fewer
- **Doctor efficiency** - EMR loads in <2 seconds

---

## Key Documents

- Business Goals: `Document/01_Business/HCMS_Business_Goals_v0.1.html`
- Project Structure: `Templates/project_structure_template.md`
- CLAUDE.md: Repository-specific AI guidance

---

## Decisions Log

*(Empty - will track major decisions as they are made)*

---

**Remember**: When in doubt, ask "Would a pediatric clinic with 10 patients/day actually need this?"
