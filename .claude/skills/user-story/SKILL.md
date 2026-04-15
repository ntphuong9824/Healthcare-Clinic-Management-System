# User Story Skill

## Trigger

Use when user asks to generate/write/create a User Story.

---

## User Story Format

When generating User Stories, STRICTLY use this format:

```markdown
## Epic: [Epic Name]
**User Story:** As a [Role], I want to [Action], so that [Value].

**Acceptance Criteria:**
- Scenario 1: [Name]
  - **Given** [Precondition]
  - **When** [Trigger]
  - **Then** [Expected Outcome System State]
- Scenario 2: [Name]
  - **Given** [Precondition]
  - **When** [Trigger]
  - **Then** [Expected Outcome System State]
```

**Rules:**
- Epic groups related user stories by feature area (Booking, EMR, Billing)
- Role must match Glossary: `Parent`, `Receptionist`, `Physician`, `Admin`
- Value should tie back to Business Vision (efficiency, digitization, self-service)
- Acceptance Criteria must include at least 2 scenarios: Happy Path + 1 Unhappy Path
- Always number scenarios: "Scenario 1:", "Scenario 2:", etc.

**Example:**
```markdown
## Epic: Self-Service Appointment Booking
**User Story:** As a Parent, I want to view available appointment time slots, so that I can choose a convenient time for my child's visit.

**Acceptance Criteria:**
- Scenario 1: View available slots for next 7 days (Happy Path)
  - **Given** I am on the booking portal homepage
  - **When** I select a future date within the next 7 days
  - **Then** I see a grid of available time slots for all physicians
- Scenario 2: No slots available on selected date (Unhappy Path)
  - **Given** I select a date with no available appointments
  - **When** the system loads the schedule
  - **Then** I see a message "No appointments available on this date" and suggestions for nearby dates
```
