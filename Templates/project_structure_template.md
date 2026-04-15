# Project Structure Template - SLLS

This document describes the standard folder structure for the SLLS (Smart Library and Learning System) project.

## Project Root Structure

```
SLLS/
├── .claude/                 # Claude Code configuration
├── .idea/                   # IntelliJ IDEA project files
├── .omc/                    # Oh-My-Claudecode state and configuration
├── Developments/            # Development workspace and code
├── Document/               # Project documentation
│   ├── 00_Workflows/
│   ├── 01_Business/
│   │   └── Personas/
│   ├── 02_Requirements/
│   │   ├── Use Cases/
│   │   └── Workflows/
│   ├── 03_Design/
│   │   ├── 01_Architecture/
│   │   ├── 02_Database_Design/
│   │   └── 03_UIUX/
│   └── 04_Project_Management/
│       ├── Meeting Notes/
│       └── Plans/
├── Templates/              # Project templates and boilerplates
└── Testing/                # Test files and test documentation
    ├── 01_UT/             # Unit Tests
    └── 02_IT/             # Integration Tests
```

## Directory Descriptions

### `/Document` - Main Documentation Folder

The Document folder is organized into numbered categories for easy navigation and consistent ordering.

#### `00_Workflows/`
General workflows and processes used in the project.

**Contents:**
- Development workflows
- Deployment workflows
- Review processes
- Team coordination procedures

#### `01_Business/`
Business-related documentation.

**Subdirectories:**
- `Personas/` - User personas and profiles

**Contents:**
- Stakeholder analysis
- Business requirements
- User stories
- Market analysis

#### `02_Requirements/`
Functional and non-functional requirements.

**Subdirectories:**
- `Use Cases/` - Detailed use case descriptions
- `Workflows/` - User workflows and process flows

**Contents:**
- Functional requirements (FR)
- Non-functional requirements (NFR)
- Use case diagrams and descriptions
- User journey maps
- Acceptance criteria

#### `03_Design/`
System and UI/UX design documentation.

**Subdirectories:**
- `01_Architecture/` - System architecture diagrams and decisions
- `02_Database_Design/` - Database schemas and ER diagrams
- `03_UIUX/` - User interface and experience designs

**Contents:**
- Architecture diagrams (C4 model, component diagrams)
- Database schemas
- API designs
- Wireframes and mockups
- Style guides

#### `04_Project_Management/`
Project planning and tracking documents.

**Subdirectories:**
- `Meeting Notes/` - Meeting minutes and notes
- `Plans/` - Project plans, timelines, and roadmaps

**Contents:**
- Project charter
- Sprint plans
- Milestone tracking
- Risk registers
- Status reports

### `/Developments/`
Active development workspace. This folder typically contains:
- Source code
- Build outputs
- Development configurations
- Feature branches or work-in-progress code

**Recommended internal structure:**
```
Developments/
├── src/
│   ├── components/     # Reusable UI components
│   ├── pages/         # Page components / routes
│   ├── layouts/       # Layout wrappers
│   ├── hooks/         # Custom React hooks
│   ├── utils/         # Utility functions
│   ├── services/      # API service calls
│   ├── stores/        # State management
│   ├── types/         # TypeScript definitions
│   └── styles/        # CSS/SCSS files
├── public/            # Static assets
├── tests/             # Test files
├── package.json
├── tsconfig.json
└── README.md
```

### `/Templates/`
Reusable templates for documents, code, and configurations.

**Contents:**
- Document templates (requirements, design docs)
- Code templates (component templates, API endpoints)
- Configuration templates (docker, CI/CD)
- Report templates

**Subdirectories (suggested):**
```
Templates/
├── documents/
├── code/
│   ├── components/
│   ├── api/
│   └── tests/
└── config/
```

### `/Testing/`
Test-related files and documentation.

#### `01_UT/` - Unit Tests
- Component unit tests
- Utility function tests
- Hook tests
- Mock data and fixtures

**Structure:**
```
01_UT/
├── __tests__/          # Test files
├── fixtures/          # Test fixtures and mock data
├── setup/             # Test setup and configuration
└── coverage/          # Coverage reports (generated)
```

#### `02_IT/` - Integration Tests
- API integration tests
- End-to-end tests
- System tests
- Performance tests

**Structure:**
```
02_IT/
├── e2e/              # End-to-end tests
├── api/              # API tests
├── fixtures/         # Shared test fixtures
└── reports/          # Test reports (generated)
```

### Configuration Folders (Hidden)

#### `.claude/`
Claude Code AI assistant configuration and memory files.

#### `.idea/`
IntelliJ IDEA or VS Code project configuration. Should be in `.gitignore`.

**Contents:**
- Project settings
- Run configurations
- Workspace files

#### `.omc/`
Oh-My-Claudecode state, sessions, and plugin configuration.

**Contents:**
- `state/` - Session state and HUD configuration
- `notepad.md` - Agent scratchpad
- `project-memory.json` - Project context memory
- `plans/` - Saved implementation plans

## Naming Conventions

### Folders
- Use kebab-case: `use-cases`, `project-management`
- Prefix with numbers for ordered sections: `00_`, `01_`, `02_`
- Keep names descriptive but concise

### Files
- Documents: `requirement-spec-v1.2.md`
- Code: `user-profile.tsx`, `api-client.ts`
- Tests: `button.test.tsx`, `api-integration.test.ts`

## Best Practices

### 1. Documentation Organization
- Use numbered prefixes for consistent ordering
- Keep related documents together in the same folder
- Use clear, descriptive file names
- Include version numbers for major documents

### 2. Code Organization
- Group by feature or domain for larger projects
- Keep components co-located with their tests and styles when possible
- Use barrel exports (`index.ts`) to simplify imports
- Separate business logic from UI components

### 3. Testing Structure
- Mirror the source structure in test folders
- Use descriptive test names: `should render user name when provided`
- Keep test data and fixtures separate from test logic
- Tag tests by type: unit, integration, e2e

### 4. Version Control
- Exclude IDE files (`.idea/`)
- Exclude dependency folders (`node_modules/`)
- Exclude build outputs and logs
- Include only source code and documentation

## Template Recommendations

When starting a new project or module, consider using this structure:

```
project-name/
├── README.md
├── CHANGELOG.md
├── CONTRIBUTING.md
├── .gitignore
├── docs/              # Additional documentation
│   ├── api/
│   ├── architecture/
│   └── deployment/
├── src/
│   ├── features/      # Feature-based organization
│   │   ├── auth/
│   │   ├── dashboard/
│   │   └── reports/
│   ├── shared/
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── utils/
│   │   └── types/
│   └── app/           # App router setup
├── test/
│   ├── unit/
│   ├── integration/
│   └── fixtures/
├── .env.example
├── package.json
├── tsconfig.json
├── tailwind.config.js
└── next.config.js
```

## Notes

- This structure is designed for a Next.js/React + TypeScript project
- Adjust based on framework choice (Vue, Angular, etc.)
- Document structure can be adapted for non-web projects
- Keep the structure simple and evolve it as needed

---

*Last updated: 2025-04-13*
*Project: SLLS (Smart Library and Learning System)*