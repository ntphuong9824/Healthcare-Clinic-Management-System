# Development Workflow

This document outlines the development setup, testing strategy, and technology considerations for the HCMS project.

## Setting Up Development

The `Developments/` directory is currently empty. When starting implementation:

1. **Choose a tech stack** (recommendation: Next.js + React + TypeScript)
2. **Initialize the project** following the structure in `Templates/project_structure_template.md`
3. **Configure build tools** (Vite, Next.js, or similar)
4. **Set up testing framework** (Jest/Vitest for unit tests, Playwright/Cypress for E2E)
5. **Configure linting** (ESLint for TypeScript/JavaScript, Prettier for formatting)

## Testing Strategy

### Unit Tests (01_UT/)
- Location: `Testing/01_UT/` (mirror `src/` structure)
- Purpose: Test individual components, utilities, hooks in isolation
- Framework: Jest or Vitest recommended
- Coverage target: 80%+ for business logic

### Integration Tests (02_IT/)
- Location: `Testing/02_IT/`
- Purpose: API endpoint tests, end-to-end user workflows, database integration
- Framework: Playwright or Cypress for E2E; Supertest for API
- Focus: Critical user journeys (booking flow, EMR access, checkout)

### Running Tests

Commands will be determined based on chosen tech stack:

```bash
# Unit tests
npm test              # or: yarn test
npm run test:watch    # watch mode
npm run test:coverage # coverage report

# Integration/E2E tests
npm run test:integration
npm run test:e2e

# All tests
npm test -- --all
```

## Development Commands (To Be Configured)

Once the tech stack is selected, standardize on:

| Task | Command |
|------|---------|
| Start dev server | `npm run dev` |
| Build for production | `npm run build` |
| Run linter | `npm run lint` |
| Fix lint issues | `npm run lint:fix` |
| Run all tests | `npm test` |
| Run unit tests | `npm run test:unit` |
| Run E2E tests | `npm run test:e2e` |

## Technology Stack (Considerations)

No tech stack has been officially selected yet. Recommendations based on project needs:

### Frontend
- **Framework**: Next.js 14+ (App Router) or React 18+
- **Language**: TypeScript (strict mode)
- **Styling**: Tailwind CSS for rapid UI development
- **State management**: React Context or Zustand (keep it simple)
- **Forms**: React Hook Form with Zod validation

### Backend
- **Option 1**: Next.js API routes (full-stack simplicity)
- **Option 2**: Separate Node.js/Express API (more control, more complexity)
- **Recommendation**: Start with Next.js API routes for MVP speed

### Database
- **Development**: SQLite (zero config, file-based)
- **Production**: PostgreSQL (reliable, healthcare-ready)
- **ORM**: Prisma (type-safe, easy migrations) or Drizzle (lightweight)
- **Why relational**: All 5 entities have clear relationships; no need for document store

### Testing
- **Unit**: Jest or Vitest
- **E2E**: Playwright (excellent for booking workflows)
- **Mocking**: MSW (Mock Service Worker) for API mocking

### Deployment (Future)
- **Platform**: Vercel (for Next.js) or Railway/Render for Node.js
- **Database**: Supabase PostgreSQL or Neon
- **Environment**: `.env.local` for secrets; never commit credentials

## Performance Targets

Given the small scale (1-2 doctors, 10-20 patients/day):

- **Booking page load**: <2 seconds
- **EMR patient history fetch**: <1 second
- **Checkout flow**: <3 clicks to complete
- **Concurrent users**: <50 (low scale, no heavy optimization needed)

## Security Considerations

- **PHI protection**: All patient data is Protected Health Information
- **Encryption**: Encrypt data at rest; use HTTPS in transit
- **Access control**: Role-based (Parent, Receptionist, Physician, Admin)
- **Audit trail**: Log who accessed/modified patient records (for compliance)
- **No patient passwords** in MVP: Parents won't have portal logins (self-booking via unique links or phone)

---

**Related:** See `.claude/project-memory.md` for current project state and next steps.
