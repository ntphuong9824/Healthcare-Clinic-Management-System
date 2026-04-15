# Code Conventions

This document defines the coding standards and conventions for the HCMS project.

## File Organization

- **Feature-first or domain-first** organization
- Example structure:
  ```
  src/
  ├── booking/     # Appointment scheduling features
  ├── emr/         # Electronic medical records
  ├── billing/     # Payment and invoicing
  └── shared/      # Shared utilities, components, types
  ```
- Co-locate components with their tests and styles when possible
- Use barrel exports (`index.ts`) to simplify imports
- Separate business logic from UI components

## Naming Conventions

### Files and Folders
- Use **kebab-case** for folders: `use-cases`, `project-management`
- Use descriptive names for files: `user-profile.tsx`, `api-client.ts`, `format-date.ts`

### Components (React/UI)
- **PascalCase** for React components: `BookingCalendar.tsx`, `PatientForm.tsx`
- Keep component names descriptive but concise

### Functions and Utilities
- **camelCase** for functions: `formatDateTime()`, `calculateFee()`, `validatePatient()`
- Use verb-first naming for actions: `createAppointment()`, `fetchPatientHistory()`

### Types and Interfaces
- **PascalCase** for types/interfaces
- Optional: prefix with `I` for interfaces (be consistent): `IPatient`, `IAppointment`
- Enum names: `PascalCase` with SCREAMING values: `enum AppointmentStatus { Pending, Confirmed }`

### Database
- **SCREAMING_SNAKE_CASE** for tables, matching entity names: `PATIENT`, `APPOINTMENT`, `VISIT`
- Columns: snake_case matching data field specs: `date_of_birth`, `parent_contact_phone`

## Testing

### Test File Naming
```
[component|unit|integration]/[should behavior] when [condition].test.[ts|tsx|py]
```
**Examples:**
- `BookingCalendar/should-display-available-slots.test.tsx`
- `utils/should-format-date-correctly.test.ts`
- `api/should-create-appointment.when-valid-data.test.ts`

### Test Structure
- Mirror the `src/` directory structure in `Testing/01_UT/`
- Use descriptive test names that explain the expected behavior
- Include fixtures and mock data in separate directories

## Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
type(scope): subject

body

BREAKING CHANGE: (if applicable)
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `test`: Adding or updating tests
- `refactor`: Code restructuring (no functional changes)
- `chore`: Build/CI changes, dependency updates

**Scope examples:** `booking`, `emr`, `billing`, `database`, `auth` (if added)

**Example:**
```
feat(booking): add appointment time slot grid

- Implement calendar view showing available slots
- Support filtering by physician
- Disable past dates automatically

BREAKING CHANGE: None
```

## Pull Request Template

```markdown
## Summary
[What changed and why - 1-2 sentences]

## Changes
- [ ] Feature A implementation
- [ ] Bug fix B resolution
- [ ] Test coverage added

## Test Plan
- [ ] Unit tests pass (`npm test`)
- [ ] Integration tests pass (`npm run test:integration`)
- [ ] Manual testing completed:
  - [ ] Booking flow works for parents
  - [ ] EMR displays patient history correctly
  - [ ] Billing generates invoices accurately

## Screenshots (if UI changes)
[Attach screenshots showing the changes]

## Related Issue
Closes #[issue_number]
```

## Code Quality Rules

1. **No magic numbers/strings**: Use constants or enums for repeated values
2. **Single Responsibility**: Each function/component does one thing well
3. **Error handling**: Validate inputs and handle edge cases explicitly
4. **Type safety**: Leverage TypeScript's type system; avoid `any`
5. **PHI protection**: Never log sensitive patient data; use redaction in logs

## Database Conventions

- Table names: `SCREAMING_SNAKE_CASE` matching entity names
- Foreign keys: `[referenced_table]_id` (e.g., `patient_id`, `appointment_id`)
- Timestamps: `created_at`, `updated_at` (ISO 8601 format)
- Soft deletes: Use `deleted_at` column (nullable) instead of physical deletes
- Indexes: Add on frequently queried columns (`patient_id`, `date_time_slot`, `status`)

---

**Related:** See `.claude/skills/user-story/SKILL.md` for user story formats that drive feature implementation.
