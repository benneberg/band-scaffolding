# BMAD Scaffold: Open Specifications Document

**Version:** 1.1.0  
**Status:** Active Development  
**Last Updated:** January 2026  
**Author:** Lukas Benneberg

---

## 1. Project Overview

### 1.1 Introduction

BMAD Scaffold is a mobile-first web application that enforces the BMAD (Build, Make, Architect, Deploy) discipline on software development projects. The application serves as a meta-tool that allows users to spin up small, time-boxed micro-projects while observing and practicing the complete BMAD lifecycle. The core philosophy driving this application is that meaningful learning comes from repeated practice within a structured framework, rather than theoretical discussion alone.

The application addresses a critical gap in modern software development education and practice: the tendency to dive directly into coding without proper planning, architectural design, or quality assurance. By enforcing explicit stages and requiring artifacts at each phase, BMAD Scaffold ensures that users develop disciplined habits that translate into higher-quality software and more predictable project outcomes. The mobile-first approach recognizes that modern development teams often need to manage projects and review progress from mobile devices, making accessibility a primary design constraint rather than an afterthought.

The target audience for BMAD Scaffold includes solo developers looking to improve their practice, teams onboarding new members to structured development methodologies, and individuals exploring AI-assisted development workflows. The application does not aim to replace human judgment or serve as a fully autonomous development system; instead, it provides scaffolding that guides human decision-making while leveraging AI agents to accelerate artifact generation and exploration.

### 1.2 Core Philosophy

The fundamental insight behind BMAD Scaffold is that process discipline becomes meaningful only when practiced repeatedly on small, manageable projects. Large enterprise projects often obscure the true value of methodology because their complexity introduces too many variables. By constraining projects to micro scopesâCRUD APIs, simple CLI tools, basic IoT device registriesâthe application creates an environment where the impact of each BMAD phase can be observed clearly and patterns can be identified through repetition.

This approach draws from deliberate practice research, which suggests that expertise develops through focused repetition with immediate feedback. Each micro-project serves as a learning opportunity where users can experiment with different planning techniques, architectural patterns, and quality assurance strategies. The artifacts generated during each phase become reference material that users can review to understand how their decisions played out over time.

### 1.3 Project Goals

BMAD Scaffold pursues several interconnected goals that together create a comprehensive learning and project management environment. The primary goal is to enforce a structured workflow that prevents premature coding, ensuring that every project progresses through explicit planning, architecture, execution, and quality assurance stages. This enforcement is not merely advisory; the application requires completion of artifacts before advancing phases, making process compliance a fundamental aspect of the user experience.

The secondary goal involves artifact preservation and context maintenance. Many development tools treat planning documents, architecture diagrams, and QA reports as disposable byproducts of the "real work" of coding. BMAD Scaffold treats these artifacts as first-class entities that persist throughout the project lifecycle and remain accessible during subsequent phases. This persistent artifact store creates a complete project history that supports retrospective analysis and continuous improvement.

The tertiary goal addresses AI integration in development workflows. Rather than positioning AI as a replacement for developer thinking, BMAD Scaffold treats AI agents as assistants that accelerate artifact generation while leaving final decisions to human users. The prompt templates embedded in the Agent Runner system demonstrate how to structure effective prompts for different development contexts, teaching users valuable skills for AI-assisted development.

The quaternary goal, which distinguishes BMAD Scaffold from conventional project management tools, is learning amplification. The system explicitly captures and extracts insights from each project, enabling pattern recognition across multiple projects and longitudinal improvement over time. This metacognitive dimension transforms BMAD Scaffold from a simple project tracker into a deliberate practice system for software development skills.

---

## 2. Design System

### 2.1 Design Principles

The BMAD Scaffold interface follows a mobile-first design philosophy that prioritizes touch-based interaction, information density appropriate for small screens, and clear visual hierarchy. Every design decision traces back to the principle that the application must function effectively on devices with 375-pixel-wide viewports while remaining comfortable on desktop displays. This constraint drives simplification of navigation patterns, reduction of chrome and decorative elements, and careful attention to touch target sizing.

Accessibility forms the second design principle, ensuring that users with varying abilities can interact with the application effectively. The high-contrast dark theme reduces eye strain during extended use while maintaining readability across lighting conditions. Color is used purposefully to convey meaningâphase status, action types, and interactive statesârather than decoration. Typography employs generous line heights and adequate character spacing to support users with visual processing differences.

Performance represents the third design principle, acknowledging that mobile users may operate on limited bandwidth or processing power. The application achieves responsiveness through careful resource management, avoiding heavy framework dependencies and optimizing rendering paths. The offline-first architecture ensures that core functionality remains available during network interruptions, with graceful degradation for features requiring connectivity.

Progressive disclosure forms the fourth design principle, recognizing that new users face significant cognitive load from BMAD concepts, agents, artifacts, and phases. The application provides sensible defaults and gradual complexity revelation, allowing users to master fundamentals before encountering advanced features. Experienced users can enable additional capabilities through explicit configuration.

### 2.2 Color System

The color palette establishes a cohesive visual language that communicates project status, interactive states, and informational hierarchy throughout the application. The foundation rests on slate grays that create depth and separation without competing for attention with content.

**Background Colors:**

The application employs a carefully calibrated dark theme based on Tailwind CSS color scales. The primary background uses `#0f172a` (slate-900), creating a deep, dark surface that reduces eye strain and provides excellent contrast for text content. Secondary backgrounds employ `#1e293b` (slate-800) for cards, modals, and elevated surfaces, creating subtle depth differentiation. Interactive elements and selection states use `#334155` (slate-700) to indicate interactivity while maintaining harmony with the overall palette.

**Phase Status Colors:**

Each BMAD phase carries a distinct color that appears consistently across the interfaceâin status badges, progress indicators, and accent elements. Planning phase uses `#f59e0b` (amber), evoking the exploratory nature of initial planning. Architecture phase employs `#8b5cf6` (violet), suggesting the systematic and structural nature of design work. Execution phase uses `#10b981` (emerald), symbolizing active construction and growth. QA phase employs `#3b82f6` (blue), representing the analytical and verification-focused nature of testing. The Done phase uses `#6b7280` (gray), indicating completion and stability.

**Action Colors:**

Primary actionsâthe most important interactive elements on any screenâuse `#3b82f6` (blue-500) to signal importance without aggressive contrast. Destructive actions employ `#ef4444` (red-500) with accompanying confirmation flows to prevent accidental data loss. Success states use `#10b981` (emerald-500) to confirm positive outcomes. Warning states use `#f59e0b` (amber-500) to draw attention without alarming users.

### 2.3 Typography

Typography choices balance readability, information density, and aesthetic appeal within the constraints of mobile-first design. The primary typeface, Inter, provides excellent legibility at small sizes while supporting weights that create clear visual hierarchy. This system font stack prioritizes native rendering performance while falling back gracefully across platforms.

The type scale follows a modular approach with base size 16px (14px for secondary text and code). Headings employ 600 and 700 weights to establish clear hierarchy, while body text uses 400 weight with generous line height of 1.7 for comfortable reading. The type scale ramps down for metadata, timestamps, and auxiliary information, preventing visual competition with primary content.

Code and artifact content employ monospace typography using system monospace fonts. This distinction signals the special nature of code blocks, user stories, and markdown content while maintaining readability across different platforms. Code blocks within artifacts use slightly smaller base size (14px) to accommodate longer lines within mobile viewports.

### 2.4 Component Architecture

**Header Component:**

The sticky header provides constant access to navigation and contextual actions while remaining unobtrusive during content consumption. The header adapts its contents based on the current viewâshowing back navigation when drilling into project details, displaying project name when viewing a specific project, and presenting simplified branding on the home screen. The header height of 60px balances content visibility with touch target accessibility.

**Project Card Component:**

Project cards serve as the primary entry point to project details, displaying essential information at a glance while inviting interaction. Cards employ a rounded rectangle shape (16px border radius) with subtle border treatment that provides definition without visual heaviness. The card layout prioritizes project name and status, with description truncated to prevent overflow. Tech stack tags appear as small pills below the description, allowing users to quickly assess technology choices. A progress bar beneath the tags provides visual feedback on phase completion.

**Phase Stepper Component:**

The phase stepper communicates project position within the BMAD lifecycle through a horizontally arranged sequence of phase indicators. Completed phases display with filled circles and green coloring, while the current phase emphasizes with a larger, ringed indicator. Future phases appear as outlined circles with muted coloring. Connection lines between phases indicate sequential relationship while the progress bar fills proportionally based on current position.

**Phase Readiness Indicator:**

The phase stepper includes visual indicators when a phase is entered without adequate preparation. If a user advances to Architecture without a Planning artifact, the Architecture indicator displays a warning icon and the stepper shows a subtle amber border. These indicators communicate "soft enforcement" without blocking progress, preserving user autonomy while highlighting potential issues.

**Artifact List Component:**

Artifact lists present project artifacts in a scrollable vertical arrangement, supporting quick scanning and selection. Each artifact entry uses a consistent layout with type icon, filename, agent role, and timestamp. Touch targets extend to the full row height, accommodating imprecise touch input while maintaining visual clarity. Empty states provide guidance when no artifacts exist, reducing user confusion.

**Artifact Completeness Badge:**

Artifact items in the list display a small completeness indicator if the artifact meets minimum requirements. For example, a PRD with required sections shows a checkmark, while one missing sections shows a warning icon. This provides at-a-glance feedback on artifact quality without requiring users to open each artifact.

**Modal Components:**

Modals handle focused tasks requiring user attention without navigating to new screens. Create project modal, artifact editor modal, and various action modals share consistent presentation with rounded corners, backdrop blur, and clear action buttons. Modal height adapts to content while maintaining scrollability for long forms. Touch targets within modals meet minimum 44px requirements for accessibility.

---

## 3. Technical Architecture

### 3.1 Technology Stack

BMAD Scaffold employs a deliberately minimal technology stack that prioritizes reliability, performance, and maintainability over feature richness. The application is implemented as a single HTML file containing all markup, styles, and JavaScript, enabling deployment simplicity and reducing the attack surface associated with complex build processes.

**Core Technologies:**

The frontend layer uses plain JavaScript (ES6+) without framework dependencies, reducing bundle size and eliminating learning curve barriers for contributors. This decision aligns with the project's philosophy of starting small and avoiding premature optimization. State management occurs through a centralized StateManager object that provides predictable mutation patterns.

Styling leverages Tailwind CSS via CDN for rapid development and consistent design token application. The CDN approach sacrifices some performance for development convenience and deployment simplicity; future iterations may adopt a build process with tree-shaking for production optimization. Phosphor Icons provides a consistent icon vocabulary through a lightweight CDN import, supporting the application's visual language without requiring icon asset management.

Markdown rendering employs Marked.js for converting artifact content to HTML for display. This library provides reliable parsing with security considerations for untrusted input. The combination of CDN-served libraries creates a self-contained application that loads quickly and operates reliably across browser environments.

### 3.2 Storage Layer

The storage layer provides abstraction over persistence mechanisms, enabling future migration without application code changes.

**StorageAdapter Interface:**

```javascript
const Storage = {
    load(key) {
        // Returns parsed data or null
    },
    save(key, data) {
        // Persists data, returns success boolean
    },
    clear(key) {
        // Removes data, returns success boolean
    },
    export() {
        // Returns all data as portable format
    },
    import(data) {
        // Merges imported data, returns success boolean
    }
}
```

The StorageAdapter currently wraps localStorage but provides a migration path for IndexedDB, cloud storage, or file-based persistence. All application code accesses storage exclusively through this interface, isolating persistence details from business logic.

**Current Implementation (localStorage):**

```javascript
const LocalStorageAdapter = {
    load(key) {
        try {
            const stored = localStorage.getItem(key);
            return stored ? JSON.parse(stored) : null;
        } catch (error) {
            console.error('Storage load error:', error);
            return null;
        }
    },
    save(key, data) {
        try {
            localStorage.setItem(key, JSON.stringify(data));
            return true;
        } catch (error) {
            console.error('Storage save error:', error);
            return false;
        }
    },
    clear(key) {
        localStorage.removeItem(key);
    },
    export() {
        const data = {};
        for (let i = 0; i < localStorage.length; i++) {
            const key = localStorage.key(i);
            data[key] = JSON.parse(localStorage.getItem(key));
        }
        return data;
    },
    import(data) {
        for (const [key, value] of Object.entries(data)) {
            localStorage.setItem(key, JSON.stringify(value));
        }
        return true;
    }
};
```

### 3.3 State Management

Application state resides in a centralized StateManager object that provides controlled mutation through explicit methods. This approach replaces direct variable manipulation, ensuring all state changes are traceable and debuggable.

**StateManager Interface:**

```javascript
const StateManager = {
    // State access (read-only)
    getState() { return deepClone(state); },
    
    // Project operations
    createProject(projectData) { ... },
    updateProject(id, updates) { ... },
    deleteProject(id) { ... },
    setCurrentProject(id) { ... },
    
    // Artifact operations
    createArtifact(projectId, artifactData) { ... },
    updateArtifact(projectId, artifactId, updates) { ... },
    deleteArtifact(projectId, artifactId) { ... },
    
    // Phase operations
    advancePhase(projectId) { ... },
    setPhase(projectId, phase) { ... },
    
    // Persistence
    persist() { return Storage.save(STORAGE_KEY, projects); },
    load() { projects = Storage.load(STORAGE_KEY) || []; }
};
```

All mutating methods follow a consistent pattern: validate inputs, update in-memory state, trigger any registered observers, and persist to storage. This pattern enables future features like undo/redo, state history, and change notifications.

### 3.4 Application Structure

The application follows a single-page architecture where all functionality operates within a single HTML document. Navigation between views occurs through DOM manipulation that shows and hides sections based on application state, avoiding full page reloads that would interrupt user workflow.

**View Hierarchy:**

The home view displays the project registry, showing statistics and project cards for all stored projects. From here, users can access the create project flow or open existing projects. The project detail view presents comprehensive information about a single project, including status, tech stack, phase progress, artifacts, and agent runner. The artifact view enables editing and viewing of individual artifact content. Agent prompt views display generated prompts for copying to clipboard.

**Observer Pattern:**

The StateManager supports an observer pattern for UI updates:

```javascript
const observers = new Set();

StateManager.subscribe(observerFunction) {
    observers.add(observerFunction);
    return () => observers.delete(observerFunction);
}

StateManager.notify() {
    observers.forEach(fn => fn(state));
}
```

View components subscribe to state changes and re-render when notified. This decouples state management from rendering, enabling multiple views to stay synchronized without direct coupling.

---

## 4. Data Models

### 4.1 Project Schema

Projects represent the primary organizational unit within BMAD Scaffold, grouping related artifacts and tracking progress through BMAD phases. The schema balances completeness with simplicity, capturing essential information without introducing unnecessary complexity.

```typescript
interface Project {
    id: string;
    name: string;
    description: string;
    status: 'Planning' | 'Architecture' | 'Execution' | 'QA' | 'Done';
    techStack: string[];
    createdAt: number;
    updatedAt: number;
    artifacts: Artifact[];
    settings: ProjectSettings;
}
```

**Field Descriptions:**

The `id` field provides unique identification for each project, generated using a timestamp plus random string combination. The `name` field stores the human-readable project title. The `description` field captures the project purpose and scope. The `status` field enumerates the current BMAD phase.

The `techStack` array records selected technologies from project creation. The `artifacts` array contains all artifacts associated with the project. The `settings` object stores project-specific configuration including strict mode and other preferences.

**Project Settings Schema:**

```typescript
interface ProjectSettings {
    strictMode: boolean;        // Enforce artifact requirements
    autoSave: boolean;          // Automatically persist changes
    showHints: boolean;         // Display phase readiness warnings
}
```

### 4.2 Artifact Schema

Artifacts represent the deliverables produced during each BMAD phase, serving as both work products and communication vehicles.

```typescript
interface Artifact {
    id: string;
    projectId: string;
    type: 'PRD' | 'USER_STORY' | 'ARCHITECTURE' | 'DATA_MODEL' | 'API_CONTRACT' | 'IMPLEMENTATION' | 'QA_REPORT' | 'RETROSPECTIVE';
    filename: string;
    content: string;
    agentRole: string;
    phase: string;
    timestamp: number;
    completeness: ArtifactCompleteness;
    provenance?: ArtifactProvenance;
}
```

**Completeness Tracking:**

```typescript
interface ArtifactCompleteness {
    isComplete: boolean;
    checks: CompletenessCheck[];
    lastChecked: number;
}

interface CompletenessCheck {
    name: string;
    passed: boolean;
    message: string;
}
```

Each artifact maintains completeness metadata including individual check results. Completeness checks validate structural requirements without evaluating content qualityâfor example, verifying a PRD contains an "Acceptance Criteria" header without judging whether those criteria are good.

**Provenance Tracking:**

```typescript
interface ArtifactProvenance {
    agentUsed: string;          // Which agent generated the prompt
    rawOutput?: string;         // Original AI response before editing
    promptUsed: string;         // Full prompt that was copied
    modelUsed?: string;         // Which AI model was used
    createdAt: number;          // When AI response was received
}
```

Provenance metadata preserves the AI-assisted creation context. Users may optionally store raw AI output separately from edited content, enabling comparison between AI suggestions and final decisions.

### 4.3 Artifact Validation Rules

Each artifact type has specific completeness checks that evaluate structural requirements.

**PRD Artifact:**

| Check | Description | Requirement |
|-------|-------------|-------------|
| Header Count | Must have at least 4 top-level headers | 4+ |
| Has Problem Statement | Contains problem statement section | Required |
| Has User Stories | Contains at least 3 user stories | 3+ |
| Has Acceptance Criteria | Contains acceptance criteria section | Required |
| Has Success Metrics | Contains success metrics or definition of done | Required |

**User Story Artifact:**

| Check | Description | Requirement |
|-------|-------------|-------------|
| Format Valid | Story follows "As a... I want... So that..." format | Required |
| Has Acceptance Criteria | Contains acceptance criteria section | Required |
| Has Priority | Story includes priority indication | Required |

**Architecture Artifact:**

| Check | Description | Requirement |
|-------|-------------|-------------|
| Has Component Design | Contains component or module descriptions | Required |
| Has Data Considerations | Addresses data model or storage | Required |
| Has Security Notes | Addresses security considerations | Required |
| Has API Overview | Documents API or interface design | Required |

**Implementation Artifact:**

| Check | Description | Requirement |
|-------|-------------|-------------|
| Has Code | Contains actual code or implementation | Required |
| Has Tests | Includes test coverage or test cases | Required |
| Has Comments | Code contains explanatory comments | Required |

**QA Report Artifact:**

| Check | Description | Requirement |
|-------|-------------|-------------|
| Has Test Cases | Contains structured test cases | 5+ |
| Has Edge Cases | Addresses edge cases or boundary conditions | Required |
| Has Error Scenarios | Documents error handling tests | Required |

### 4.4 Agent Prompt Templates

Agent prompts are pre-defined templates that combine project context with role-specific instructions.

```typescript
interface AgentTemplate {
    role: string;
    name: string;
    description: string;
    icon: string;
    bgColor: string;
    template: string;
}
```

**Template Substitution:**

Prompts support variable substitution using curly brace syntax: `{name}`, `{description}`, `{techStack}`, `{storyContent}`, and `{artifactContent}`. The `artifactContent` variable enables passing existing artifact content for refinement workflows.

---

## 5. BMAD Workflow

### 5.1 Phase Overview

The BMAD lifecycle consists of four primary phases plus a completion state, each producing specific artifacts and supporting different types of user activities. The workflow provides structure without rigidity, enabling users to develop their own practices within the framework.

Phase progression follows a linear path from Planning through Architecture and Execution to QA, terminating in Done. Users may advance through phases at their own pace, and the system provides feedback without blocking progress. This approach treats users as responsible adults who can make their own decisions while ensuring they have the information needed to make good choices.

### 5.2 Phase 1: Planning

The Planning phase establishes project foundation through requirements gathering and specification development. This phase emphasizes understanding the problem space before proposing solutions, establishing the "what" that subsequent phases address.

**Key Activities:**

Project creation initiates the Planning phase, establishing the project identity, scope, and technology context. During creation, users provide project name and description that inform all subsequent agent interactions. Tech stack selection enables appropriate agent prompt customization.

PRD development represents the primary Planning deliverable. The PM Agent prompt template guides comprehensive PRD creation including executive summary, problem statement, user personas, user stories, acceptance criteria, and success metrics. Users generate prompts, interact with AI assistants, and create PRD artifacts that capture project requirements.

User story development complements the PRD by breaking down features into manageable units. The Scrum Master Agent helps decompose high-level requirements into discrete stories suitable for implementation.

**Phase Readiness Indicators:**

When entering the Planning phase, the system checks for required artifacts. For first-time users or when hints are enabled, the system displays guidance on what a good Planning phase outcome looks like. No blocking occurs, but awareness is raised.

### 5.3 Phase 2: Architecture

The Architecture phase translates requirements into technical specifications, establishing the "how" that guides implementation. This phase emphasizes systematic design that anticipates implementation challenges and establishes clear structural patterns.

**Key Activities:**

Architecture document development produces the primary Architecture deliverable, specifying system components, data models, API contracts, and technology decisions. The Architect Agent prompt template guides comprehensive architecture design.

Data model design specifies the information structures that support project requirements. Users create data model artifacts that define entities, relationships, constraints, and migrations.

API contract development establishes interface specifications for system components and external integrations. Users create API contract artifacts documenting endpoints, request/response formats, authentication requirements, and error handling.

**Phase Readiness Warnings:**

If a user advances to Architecture without completing Planning artifacts, a warning appears: "Architecture phase entered with no PRD found. Consider completing planning before proceeding." The warning is informational, not blocking.

### 5.4 Phase 3: Execution

The Execution phase transforms specifications into working code, implementing features described in user stories against architectural patterns established in design documents.

**Key Activities:**

Story-by-story implementation breaks the project into manageable units. The Dev Agent prompt template provides context-specific coding assistance, generating implementation artifacts based on user story content and architectural specifications.

Code quality maintenance ensures that implementations meet standards established in architecture documents. The QA Agent may be engaged during Execution to validate implementations against requirements.

### 5.5 Phase 4: QA

The QA phase validates implementations against requirements, identifying gaps, edge cases, and limitations.

**Key Activities:**

Test case development creates structured verification plans. The QA Agent prompt template guides comprehensive test case generation including happy path scenarios, edge conditions, error handling, and security tests.

Edge case identification surfaces scenarios that standard testing might miss, improving deliverable robustness.

### 5.6 Completion State

The Done state represents project completion, indicating that all planned work has been completed and quality standards have been met. Projects in Done state remain accessible for reference but no longer appear in active workflow queues.

**Retrospective Trigger:**

When advancing to Done, the system offers to create a Retrospective artifact. This artifact guides users through reflection on the project, capturing insights that inform future improvements. The retrospective is optional but strongly recommended for users seeking to maximize learning value.

---

## 6. Agent Runner System

### 6.1 Agent Overview

The Agent Runner system provides structured prompts for six specialized roles that support different BMAD activities. Each agent combines role-specific instructions with project context to generate useful artifacts. The system does not execute agent actions directly; instead, it generates prompts that users copy to external AI assistants and creates artifacts from returned responses.

**Design Philosophy:**

The agent system follows a human-in-the-loop design where AI accelerates artifact generation while humans retain control over quality and decisions. This approach treats AI as an assistant rather than an autonomous agent, leveraging AI capabilities for exploration and drafting while relying on human judgment for refinement and approval.

### 6.2 Agent Descriptions

**Analyst Agent:**

The Analyst Agent supports requirement discovery and analysis, helping users articulate needs and identify implicit assumptions. This agent excels at breaking down vague ideas into structured requirements, surfacing potential risks, and defining success metrics.

**PM Agent:**

The PM (Product Manager) Agent transforms analyzed requirements into formal product specifications. This agent generates comprehensive PRD documents including executive summary, problem statement, user personas, user stories with acceptance criteria, success metrics, and timeline estimates.

**Architect Agent:**

The Architect Agent translates requirements into technical specifications, designing system structures that satisfy functional and non-functional requirements. This agent produces architecture overview documents, component designs, data models, API contracts, security considerations, and scalability strategies.

**Dev Agent:**

The Dev (Developer) Agent supports implementation activities, generating code artifacts based on user stories and architectural specifications. This agent produces implementation code, test cases, and related documentation following clean code principles.

**Scrum Master Agent:**

The Scrum Master Agent supports sprint planning and work breakdown, decomposing features into manageable tasks with estimates. This agent produces task breakdowns including dependencies, estimates, and definition-of-done criteria.

**QA Agent:**

The QA Agent supports verification activities, generating test cases and quality assessments. This agent produces test case documents including happy path scenarios, edge cases, error conditions, performance considerations, and security tests.

### 6.3 Agent Workflow

**Standard Workflow:**

1. User selects agent role from project detail view
2. Application builds prompt with project context
3. Prompt displays in modal with copy functionality
4. User copies prompt, pastes to AI assistant
5. User receives AI response
6. User creates artifact and pastes response

**Enhanced Workflow (Optional):**

The enhanced workflow adds provenance tracking and raw output preservation:

1. User selects agent role and enables "Track AI Output"
2. Application generates and displays prompt
3. User pastes AI response into designated field
4. Application stores raw response in provenance metadata
5. User edits content as needed
6. Both raw and edited versions persist

This enhanced workflow enables users to compare AI suggestions with final decisions, supporting the learning loop by making implicit reasoning explicit.

### 6.4 Prompt Generation

Prompt generation combines template text with project context through variable substitution.

**Template Variables:**

| Variable | Description |
|----------|-------------|
| `{name}` | Project name |
| `{description}` | Project description |
| `{techStack}` | Comma-separated tech stack |
| `{storyContent}` | Selected user story content |
| `{artifactContent}` | Current artifact content (for refinement) |

---

## 7. Artifact Management

### 7.1 Artifact Types

BMAD Scaffold supports eight artifact types, including the new Retrospective type for learning amplification.

**PRD (Product Requirements Document):**

PRD artifacts capture comprehensive product specifications including executive summary, problem statement, user personas, user stories, acceptance criteria, and success metrics. The default template provides section headers that users populate through direct editing or AI-assisted generation.

**User Story:**

User Story artifacts capture individual feature descriptions in the standard format: "As a [user type], I want to [action], so that [benefit]." The default template includes the story format plus acceptance criteria and notes sections.

**Architecture:**

Architecture artifacts capture technical design specifications including system components, data models, API contracts, security considerations, and scalability strategies.

**Data Model:**

Data Model artifacts capture information structure specifications including entity definitions, relationships, indexes, and migrations.

**API Contract:**

API Contract artifacts capture interface specifications including endpoints, request/response formats, authentication requirements, and error handling.

**Implementation:**

Implementation artifacts capture code deliverables including source code, tests, and related documentation.

**QA Report:**

QA Report artifacts capture verification results including test cases, edge cases, and known limitations.

**Retrospective (NEW):**

Retrospective artifacts capture post-project reflections, enabling learning amplification. The default template guides users through structured reflection:

```markdown
# Project Retrospective

## Project Overview
- Name: {projectName}
- Duration: {startDate} to {endDate}
- Final Phase: {finalPhase}

## What Went Well
1.
2.
3.

## What Could Be Improved
1.
2.
3.

## Key Learnings
1.
2.
3.

## Changes for Next Project
1.
2.
3.

## Overall Rating
[ ] Exceeded expectations
[ ] Met expectations
[ ] Below expectations
```

### 7.2 CRUD Operations

**Create Operations:**

Artifact creation initiates through the "Add" button on the project detail view, presenting a modal with artifact type options. Users select a type, triggering artifact instantiation with default content based on the selected type. The new artifact immediately opens in edit mode.

**Read Operations:**

Artifact reading occurs through the artifact list on the project detail view and the artifact detail view. The list provides summary information for scanning, while the detail view displays full content in rendered markdown.

**Update Operations:**

Artifact updating occurs through the edit mode toggle on the artifact detail view. Edit mode presents a textarea pre-populated with current content. Saving persists modifications and triggers completeness re-evaluation.

**Delete Operations:**

Artifact deletion occurs through the trash icon on the artifact detail view with confirmation flow to prevent accidental deletion.

### 7.3 Completeness Evaluation

The system evaluates artifact completeness when artifacts are created, updated, or viewed. Evaluation uses type-specific rules that check structural requirements without judging content quality.

**Evaluation Process:**

1. Retrieve artifact type and content
2. Apply type-specific validation rules
3. Record pass/fail for each rule
4. Calculate overall completeness score
5. Store results in artifact completeness metadata
6. Update UI indicators accordingly

**UI Feedback:**

Completeness status displays through badge indicators on artifact list items. A green checkmark indicates all checks pass. A yellow warning indicates some checks fail with opportunity for improvement. Clicking the artifact shows detailed results of each check.

### 7.4 Content Management

Artifacts store content as plain markdown text, enabling flexible formatting while maintaining portability. The Marked.js library renders markdown to HTML for display.

---

## 8. User Flows

### 8.1 Creating a Project

The create project flow establishes a new project within the BMAD Scaffold system.

**Step 1: Initiate Creation**

Users tap the "+ New" button in the application header, triggering the create project modal. The modal presents fields for project name (required), description (optional), and tech stack selection.

**Step 2: Enter Details**

Users enter project name and description. Optionally, users select tech stack items from the provided options.

**Step 3: Create Project**

Users tap "Create" to submit the form. The application generates a unique project ID, initializes the project object with default settings, adds the project to the projects array, and persists to localStorage. The application closes the modal and renders the project detail view.

### 8.2 Managing Phases

The phase management flow enables project progression through the BMAD lifecycle.

**Viewing Current Phase:**

The project detail view displays the current phase through a status badge and phase stepper. The stepper shows completed phases (green), current phase (highlighted), and future phases.

**Advancing Phase:**

Users tap the arrow button next to the status badge to advance to the next phase. The application updates the project status and re-renders with updated phase indicators. If warnings are enabled and readiness indicators suggest inadequate preparation, a warning message displays before the advance completes.

**Setting Phase Manually:**

Users may tap any phase indicator in the stepper to jump to that phase directly, supporting iterative workflows.

### 8.3 Using Agent Prompts

The agent prompt flow generates context-aware prompts for AI-assisted artifact development.

**Standard Flow:**

1. User selects agent role from the Agent Runner section
2. Application builds prompt with project context
3. Prompt displays with copy button
4. User copies prompt, pastes to AI assistant
5. User receives AI-generated content
6. User creates artifact and pastes response

**Enhanced Flow (with AI Output Tracking):**

1. User enables "Track AI Output" toggle
2. User completes standard flow steps 1-4
3. User pastes AI response into raw output field
4. Application stores raw response in provenance metadata
5. User edits content as needed in main content field
6. Both versions persist, enabling comparison later

### 8.4 Completing a Project

The project completion flow captures learnings before archiving the project.

**Step 1: Advance to Done**

User advances phase to Done through normal phase progression.

**Step 2: Retrospective Prompt**

System offers to create a Retrospective artifact with project context pre-filled. User may accept (recommended) or skip.

**Step 3: Complete Retrospective**

If accepted, user completes the retrospective template, capturing what went well, what could improve, key learnings, and changes for next project.

**Step 4: Archive**

Project enters Done state, remaining accessible for reference but moving out of active workflow queues.

---

## 9. Strict Mode

### 9.1 Overview

Strict Mode provides enhanced enforcement of BMAD discipline for users who want stronger guidance. When enabled, the application provides additional checks and warnings while still respecting user autonomy.

### 9.2 Configuration

Strict Mode is configured per project through the Project Settings modal:

```typescript
interface StrictModeSettings {
    enabled: boolean;
    requirePlanningArtifact: boolean;  // Warn if advancing without Planning artifact
    requireArchitectureArtifact: boolean;  // Block or warn without Architecture artifact
    requireQAArtifact: boolean;  // Warn if completing without QA report
    promptRetrospective: boolean;  // Require retrospective before Done
}
```

### 9.3 Behavior

**With Strict Mode Disabled (Default):**

- Phase advancement is always permitted
- Warnings display but do not block progress
- Completeness indicators are informational only
- Retrospective is optional

**With Strict Mode Enabled:**

- Warnings appear more prominently
- Some transitions may require explicit acknowledgment
- Completeness affects phase readiness visualization
- Retrospective strongly encouraged with persistent prompts

Strict Mode never blocks progress entirelyâthe application treats users as responsible decision-makers who may have legitimate reasons to proceed despite warnings.

---

## 10. Onboarding Flow

### 10.1 Progressive Disclosure

New users face significant cognitive load from BMAD concepts, agents, artifacts, and phases. The onboarding flow introduces complexity gradually, building foundational understanding before revealing advanced features.

### 10.2 First Project Experience

**Phase 1: Basic Introduction**

First-time users see simplified home view with only:
- Create Project button
- Essential header navigation
- No Agent Runner section initially

**Phase 2: Core Workflow**

After creating the first project, users see:
- Planning phase with PM Agent
- Basic artifact creation (PRD only)
- Phase stepper with all phases visible but inactive

**Phase 3: Progressive Unlocks**

As users complete phases, additional capabilities unlock:
- Architecture phase reveals Architect Agent
- Execution phase reveals Dev and Scrum Master agents
- QA phase reveals QA Agent
- Done state reveals Retrospective option

**Phase 4: Full Access**

After completing first project, all features become permanently visible with full capability access.

### 10.3 Tooltips and Guidance

Throughout the first experience, contextual tooltips provide guidance:

- First artifact creation shows inline help
- First phase advancement explains the concept
- Agent usage includes brief descriptions
- Completion triggers congratulations and encouragement

---

## 11. Technical Constraints and Considerations

### 11.1 Mobile-First Requirements

The mobile-first design approach establishes constraints that shape all implementation decisions. Viewport widths as narrow as 320 pixels must accommodate all functionality without horizontal scrolling. Touch targets must meet 44-pixel minimum dimensions for accessibility. Navigation patterns must accommodate thumb-reach zones typical of handheld device use.

### 11.2 Offline Capability

The offline-first architecture ensures core functionality remains available during network interruptions. LocalStorage persistence provides data durability without network connectivity. The application loads and renders from local resources without external dependencies beyond initial page load.

### 11.3 Browser Compatibility

The application targets modern browsers supporting ES6 JavaScript features, CSS custom properties, and the Fetch API. This includes Chrome, Firefox, Safari, and Edge versions from the past two years. Mobile browser support includes Safari on iOS and Chrome on Android.

### 11.4 Storage Limitations

LocalStorage imposes practical limits on project and artifact quantities. Typical localStorage quotas range from 5-10MB per origin, constraining text-based content storage. For micro-projects with markdown artifacts, this accommodates hundreds of projects and thousands of artifacts under normal usage patterns.

Users approaching storage limits receive notification through console logging and UI warnings. Export functionality enables data backup and storage management through manual export to JSON files.

---

## 12. Future Improvements

### 12.1 Short-Term Enhancements (v1.1 - v1.2)

**Phase A â Hardening:**

1. Implement StorageAdapter abstraction
2. Refactor StateManager with observer pattern
3. Add artifact completeness validation
4. Improve error messaging (user-facing, not alerts)
5. Add phase readiness warnings

**Phase B â Learning Amplifiers:**

6. Add Retrospective artifact type
7. Implement Strict Mode with configurable rules
8. Add enhanced agent workflow with AI output tracking
9. Add phase readiness indicators

### 12.2 Medium-Term Enhancements (v1.3 - v2.0)

**Phase C â UX Refinement:**

10. Implement progressive disclosure onboarding flow
11. Add search (projects + artifacts)
12. Add bulk operations for artifact management
13. Improve mobile gestures and interactions

**Phase D â Extensibility:**

14. Add custom agent template support
15. Add project templates for common project types
16. Add export formats (PDF, Markdown zip)

### 12.3 Long-Term Vision (v2.0+)

**Learning System Features:**

- Pattern recognition across multiple projects
- Skill progression tracking
- Personalized recommendations based on project history
- Community sharing of artifacts and templates

**Integration Features:**

- GitHub integration for artifact-to-repository workflows
- Cloud sync for multi-device access
- Collaboration features for team usage
- API for integration with external tools

---

## 13. Appendix

### 13.1 File Structure

The application exists as a single HTML file containing embedded CSS and JavaScript:

```
bmad-scaffold.html
âââ <head>
â   âââ Meta tags (viewport, theme-color, description)
â   âââ Tailwind CSS (via CDN)
â   âââ Phosphor Icons (via CDN)
â   âââ Custom styles
â   âââ Inline SVG icons
âââ <body>
â   âââ Header component (sticky)
â   âââ Main content area (dynamic views)
â   â   âââ Home view (project list)
â   â   âââ Project detail view
â   â   âââ Artifact view/editor
â   â   âââ Agent prompt view
â   âââ Modal overlays
â       âââ Create project modal
â       âââ Project actions modal
â       âââ Artifact type selector
â       âââ Artifact editor modal
â       âââ Confirm dialogs
âââ <script>
    âââ StateManager (centralized state)
    âââ StorageAdapter (persistence abstraction)
    âââ Render functions (view components)
    âââ Action handlers (CRUD operations)
    âââ Agent prompts (six templates)
    âââ Completeness validators (artifact rules)
    âââ Utility functions
```

### 13.2 Dependencies

External dependencies are limited to CDN-hosted libraries:

- **Tailwind CSS** (via cdn.tailwindcss.com): Styling framework providing design tokens and utility classes
- **Phosphor Icons** (via unpkg.com/@phosphor-icons/web): Icon library providing consistent visual vocabulary
- **Marked.js** (via cdn.jsdelivr.net/npm/marked): Markdown parser for artifact rendering

### 13.3 LocalStorage Schema

Data persistence uses a single localStorage key containing a JSON-serialized array of project objects:

```json
{
  "bmad_scaffold_v1": [
    {
      "id": "proj_1704384000000_abc123",
      "name": "Example Project",
      "description": "A sample project",
      "status": "Planning",
      "techStack": ["Node.js", "PostgreSQL"],
      "createdAt": 1704384000000,
      "updatedAt": 1704384000000,
      "settings": {
        "strictMode": false,
        "autoSave": true,
        "showHints": true
      },
      "artifacts": [
        {
          "id": "art_1704384000001_def456",
          "projectId": "proj_1704384000000_abc123",
          "type": "PRD",
          "filename": "prd.md",
          "content": "# Product Requirements Document\n\n...",
          "agentRole": "PM Agent",
          "phase": "Planning",
          "timestamp": 1704384000001,
          "completeness": {
            "isComplete": false,
            "checks": [
              {"name": "Header Count", "passed": true, "message": "4 headers found"},
              {"name": "Has Problem Statement", "passed": false, "message": "Missing problem statement section"}
            ],
            "lastChecked": 1704384000001
          },
          "provenance": {
            "agentUsed": "PM Agent",
            "promptUsed": "Act as a Senior Product Manager...",
            "createdAt": 1704384000001
          }
        }
      ]
    }
  ]
}
```

### 13.4 Phase Readiness Rules

The following rules determine phase readiness indicators:

| Current Phase | Advance To | Readiness Check | Warning If |
|---------------|------------|-----------------|------------|
| Planning | Architecture | PRD exists with completeness score > 50% | No PRD or PRD incomplete |
| Architecture | Execution | Architecture artifact exists | No architecture artifact |
| Execution | QA | At least one implementation exists | No implementation artifacts |
| QA | Done | QA report exists with > 3 test cases | No QA report or minimal |

### 13.5 Complete Agent Prompt Templates

**Analyst Template:**

```
Act as a Senior Business Analyst. Analyze the following project:

**Project:** {name}
**Description:** {description}
**Tech Stack:** {techStack}

Please provide:
1. Key business requirements
2. Potential risks and challenges
3. Success metrics definition
4. Stakeholder considerations

Output your analysis as a structured markdown document.
```

**PM Template:**

```
Act as a Senior Product Manager. Create a comprehensive Product Requirements Document (PRD) for:

**Project:** {name}
**Description:** {description}
**Tech Stack:** {techStack}

Include:
1. Executive Summary
2. Problem Statement
3. User Personas (at least 2)
4. User Stories (at least 5)
5. Acceptance Criteria for each story
6. Success Metrics
7. Timeline Estimates

Format as markdown with proper headers and structure.
```

**Architect Template:**

```
Act as a Senior System Architect. Design the architecture for:

**Project:** {name}
**Description:** {description}
**Tech Stack:** {techStack}

Provide:
1. Architecture Overview (with component diagram description)
2. Component Design (modules and their responsibilities)
3. Data Model (schema definitions with examples)
4. API Contracts (endpoint definitions with request/response)
5. Security Considerations
6. Scalability Strategy

Output as markdown with code examples where appropriate.
```

**Dev Template:**

```
Act as a Senior Full-Stack Developer. Implement the following user story:

**Project:** {name}
**Tech Stack:** {techStack}

**User Story:**
{storyContent}

**Context from Architecture:**
{artifactContent}

Requirements:
- Follow clean code principles
- Include error handling
- Add appropriate comments
- Match the architecture design
- Include unit tests where applicable

Output the implementation with file paths clearly marked.
```

**Scrum Master Template:**

```
Act as a Scrum Master. Break down this feature into actionable tasks:

**Feature/Story:** {storyContent}
**Project:** {name}
**Tech Stack:** {techStack}

Provide:
1. Task breakdown with time estimates (hours)
2. Dependency identification
3. Sprint planning recommendation
4. Definition of Done for each task

Format as a structured markdown document with checkboxes.
```

**QA Template:**

```
Act as a Senior QA Engineer. Create comprehensive test cases for:

**Feature:** {storyContent}
**Project:** {name}
**Tech Stack:** {techStack}

Include:
1. Happy path test cases (main scenarios)
2. Edge cases and boundary conditions
3. Error scenarios and validation
4. Performance considerations
5. Security test cases

Output as a markdown table with columns: ID, Description, Steps, Expected Result, Priority.
```

---

## 14. Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | January 2026 | Initial specification |
| 1.1.0 | January 2026 | Added: StorageAdapter abstraction, StateManager pattern, Artifact completeness validation, Phase readiness indicators, Strict Mode, Retrospective artifact type, Enhanced agent workflow with provenance, Progressive disclosure onboarding |

---

**Document Version:** 1.1.0  
**Last Updated:** January 2026
