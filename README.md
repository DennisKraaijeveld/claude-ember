# Ember for Claude Code

## What is this?

Ember is an advanced directory-based project management system built to work seamlessly with Claude Code. It's an slimmed down version of the Simone framework, featuring a sophisticated set of folders, markdown files, and custom commands that help break down complex software projects into manageable, AI-friendly chunks.

**⚠️ Complexity Warning**: Ember is a sophisticated system that requires time to understand properly. It's not a simple plug-and-play solution, but rather a comprehensive framework that works best when you take the time to learn how it operates and adapt it to your workflow.

**📋 Latest Updates**: See [CHANGELOG.md](CHANGELOG.md) for recent changes and improvements.

## Attribution

This project is based on [@Helmi's claude-simone](https://github.com/Helmi/claude-simone), which introduced the directory-based project management approach for AI-assisted development. Ember is a streamlined version, optimized for token efficiency and tailored for complex codebase workflows.

## Prerequisites

### Zen MCP Server (Required)

Ember requires the [Zen MCP Server](https://github.com/BeehiveInnovations/zen-mcp-server) to be installed and configured, as it's essential for the code review functionality integrated into the workflow.

```bash
# Install Zen MCP Server (follow their installation guide)
# This is required for Ember's code review capabilities
```

## How to Get Started

### 1. Install Ember

```bash
npx hello-ember
```

This sets up the folder structure and installs/updates the command files in your project. Can also be used to update an existing installation - command files get backed up automatically.

### 2. Initialize Your Project

Open your project in Claude Code and run:

```
/project:ember:initialize
```

This guides you through the comprehensive setup process. Works with new or existing codebases, and can help you create detailed project documentation (PRDs, architecture docs, technical specs) or work with documents you already have.

### 3. Set Up Your First Milestone

Create a milestone folder in `.ember/02_REQUIREMENTS/` named `M01_Your_Milestone_Name` (e.g., `M01_Backend_Setup`). Include at least:

- `M01_milestone_meta.md` - Milestone metadata and overview
- `PRD_*.md` - Product requirements documents
- `SPECS_*.md` - Technical specifications

_Note: Use the existing chat from step 2 to guide Claude through milestone creation, ensuring proper naming with the `M##_` prefix and underscores.\_

### 4. Break Down into Sprints

```
/project:ember:create_sprints_from_milestone
```

This analyzes your milestone and breaks it down into logical sprints with clear boundaries. It examines the entire scope and creates meaningful sprint structures without detailed tasks yet.

### 5. Create Your First Tasks

```
/project:ember:create_sprint_tasks
```

This analyzes your sprints, reviews all documentation, researches necessary information, and identifies knowledge gaps to gain comprehensive understanding of your project. Creates detailed, actionable tasks scoped for individual Claude sessions.

_Important: Only create tasks for your next sprint, not all sprints upfront. After completing Sprint 1, then create tasks for Sprint 2. This ensures the system can reference your existing codebase and incorporate completed work into future task creation._

### 6. Start Working

```
/project:ember:do_task
```

This will automatically pick a task from your general tasks or sprints. For faster execution, specify a task ID:

```
/project:ember:do_task T01_S01
```

Claude will then work through the specified task with full project context and comprehensive understanding.

That's the basic workflow to get started! You can also:

- Create general tasks with `/project:ember:create_general_task`
- Review code quality with `/project:ember:code_review`
- Explore other commands in `.claude/commands/ember/`

**Important**: Ember is a sophisticated system, not a simple set-and-forget tool. It works best when you understand how it operates. Take time to read through the commands and consider adapting them to your workflow.

## How it Works

Ember organizes your project into a hierarchical structure:

- **Milestones**: Major features or project phases with comprehensive documentation
- **Sprints**: Groups of related tasks within a milestone with clear deliverables
- **Tasks**: Individual work items scoped for one Claude session with detailed context

Each task gets comprehensive project context so Claude knows exactly what to build, how it fits into your architecture, and what dependencies exist.

## Why Ember was Built

AI coding tools have become incredibly powerful, but they all face the same fundamental challenge: context management. The context window is limited in size, and we have little control over what stays in context and what doesn't.

The problem with long-running sessions is context decay - as you work, critical project knowledge silently falls off the end of the context window. You don't know what's been forgotten until something goes wrong.

Ember's solution: Start fresh for each task, but provide rich, structured surrounding context. By keeping tasks focused and well-scoped, we can dedicate more of the context window to relevant project knowledge, requirements, architectural decisions, and technical specifications. This way:

- Each task starts with exactly the project context it needs
- No critical knowledge gets lost in long sessions
- Claude can work confidently with full awareness of requirements and constraints
- The surrounding context guides development, not just the task description
- Complex projects remain manageable through systematic decomposition

The result is a task-based workflow where Claude always has the right context for the job at hand, with sophisticated project management capabilities.

## Key Components

### 00_PROJECT_MANIFEST.md

The central document containing the project's vision, goals, high-level overview, and current status tracking. It serves as the starting point for Claude to understand the project comprehensively. **Important**: The manifest file must be named exactly `00_PROJECT_MANIFEST.md`.

### 01_PROJECT_DOCS/

Contains comprehensive project documentation including:

- Technical architecture documentation
- API documentation with implementation details
- Development guides and conventions
- System design specifications
- Performance and optimization guides

### 02_REQUIREMENTS/

Organized by milestones, this directory stores detailed requirements documentation:

- Product Requirements Documents (PRDs)
- Technical specifications (SPECS)
- Milestone metadata with Definition of Done criteria
- Requirements amendments and updates
  Milestone folders must follow the naming convention `M##_Milestone_Name/` (e.g., `M01_Backend_Setup/`).

### 03_SPRINTS/

Contains sprint plans and task definitions organized by milestone and sprint sequence:

- Sprint metadata with goals and deliverables
- Individual task files with detailed implementation guidance
- Sprint progress tracking
- Cross-sprint dependency management

### 04_GENERAL_TASKS/

Stores task definitions for work not tied to a specific sprint:

- Completed tasks use a `TX` prefix (e.g., `TX001_Completed_Task.md`)
- Open tasks use a `T` prefix
- Cross-cutting concerns and maintenance tasks
- Technical debt and optimization work

### 99_TEMPLATES/

Contains standardized templates for consistent documentation:

- Task templates with structured objectives and acceptance criteria
- Sprint and milestone metadata templates
- ADR templates for architectural decisions
- All templates use simplified date formats (YYYY-MM-DD HH:MM)

### .claude/commands/ember/

Custom Claude Code commands that power the Ember workflow:

- `initialize` - Set up comprehensive project structure and documentation
- `create_sprints_from_milestone` - Break milestones into logical sprints
- `create_sprint_tasks` - Generate detailed tasks from sprint plans
- `do_task` - Execute individual tasks with full context
- `code_review` - Perform comprehensive code quality reviews
- `create_general_task` - Create standalone tasks for maintenance work
- And more commands for testing, reviewing, and project management

## Directory Structure

```plaintext
.ember/
├── 00_PROJECT_MANIFEST.md
├── 01_PROJECT_DOCS/
│   ├── ARCHITECTURE.md
│   ├── API_DOCS.md
│   ├── DEVELOPMENT_GUIDE.md
│   └── ...
├── 02_REQUIREMENTS/
│   ├── M01_Backend_Setup/
│   │   ├── M01_milestone_meta.md
│   │   ├── PRD_Backend_Setup.md
│   │   └── SPECS_API_V1.md
│   ├── M02_Frontend_Setup/
│   └── ...
├── 03_SPRINTS/
│   ├── S01_M01_Initial_API/
│   │   ├── sprint_meta.md
│   │   ├── T01_S01_Setup_Project_Structure.md
│   │   └── ...
│   ├── S02_M01_Database_Schema/
│   └── ...
├── 04_GENERAL_TASKS/
│   ├── TX001_Refactor_Logging_Module.md  # Completed task
│   ├── T002_API_Rate_Limiting.md          # Open task
│   └── ...
└── 99_TEMPLATES/
    ├── task_template.md
    ├── sprint_meta_template.md
    └── milestone_meta_template.md
```

## Configuration Tips

### Enabling Parallel Task Execution

While Ember commands like `create_sprint_tasks` support the `useParallelSubagents` instruction, Claude Code needs to be configured to actually execute tasks in parallel. By default, it only runs one task at a time.

To enable parallel execution:

```bash
# Set the number of parallel tasks (example: 3)
claude config set --global "parallelTasksCount" 3

# Check your current configuration
claude config list -g
```

**Important considerations:**

- Choose the number based on your system's capabilities and rate limits
- Parallel execution increases API usage significantly
- Some tasks may have conflicts when run in parallel
- Start with a small number (2-3) and adjust based on your experience

## Enhanced Features in Ember

### Sophisticated Project Management

- Detailed milestone tracking with Definition of Done criteria
- Sprint progress monitoring and dependency management
- Comprehensive task lifecycle management
- Advanced project state tracking

### Advanced Task Management

- Task complexity assessment and time estimation
- Cross-sprint dependency tracking
- Automated progress reporting
- Quality gate enforcement

## Contributing & Feedback

Ember represents an evolution of project management for AI-assisted development. We'd love to hear from you!

- **GitHub Issues**: Best place for bugs and feature requests
- **Pull Requests**: Very welcome! Let's make this better together
