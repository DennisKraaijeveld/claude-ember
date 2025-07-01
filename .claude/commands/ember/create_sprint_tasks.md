# Create Tasks for Sprint - Execute top to bottom

Create detailed tasks for an existing sprint with integrated implementation guidance.

## Create a TODO with EXACTLY these 6 Items

1. Identify target sprint and verify it exists
2. Load sprint context, documentation
3. Analyze sprint deliverables for task breakdown
4. Create individual task files with implementation guidance
5. Update sprint meta with task references
6. Check quality and split high complexity tasks

Follow step by step and adhere closely to the following instructions for each step.

## DETAILS on every TODO item

### 1. Identify target sprint and verify it exists

Check: <$ARGUMENTS>

**REQUIRED:** Sprint ID must be provided (e.g., S02). If empty, ask user to specify which sprint to detail.

- VERIFY sprint directory exists in `.ember/03_SPRINTS/`
- CHECK sprint meta file exists (e.g., `S02_sprint_meta.md`)
- VERIFY sprint status is not already "completed"
- If tasks already exist, ask user if they want to recreate them or any other guidance

### 2. Load sprint context, documentation

Use PARALLEL SUBAGENTS to READ and UNDERSTAND the project's context:

- READ `.ember/00_PROJECT_MANIFEST.md` for project context
- READ sprint meta file completely to understand goals and deliverables
- READ parent milestone requirements from `.ember/02_REQUIREMENTS/`
- READ `.ember/01_PROJECT_DOCS/ARCHITECTURE.md` for technical context

**IMPORTANT:** Sprint tasks must align with documented sprint goals, not expand scope.

### 3. Analyze sprint deliverables for task breakdown

Based on sprint goals and deliverables (execute in Parallel Subagents):

- BREAK DOWN high-level deliverables into concrete, implementable tasks
- ENSURE each task represents a coherent feature or component
- CONSIDER logical dependencies between tasks
- DEFER complexity assessment until after tasks are fully created

### 4. Create individual task files with implementation guidance

**NOW** For each identified Task spin up a Parallel Subagent with these Instructions:

    #### Create a TODO for EACH task

    1. Create basic task structure
    2. Research codebase interfaces
    3. Add comprehensive technical guidance
    4. Validate task completeness

    ### 1. Create basic task structure

    - ALL TASK FILES must to be created in the Sprint Directory (where the sprint meta file is)
    - CREATE file with naming: `T<NN>_S<NN>_<Descriptive_Name>.md`
    - USE sequential numbering starting from T01
    - FOLLOW task template structure exactly from `.ember/99_TEMPLATES/task_template.md`
    - ADD basic description and objectives from sprint goals

    ### 2. Research codebase interfaces

    - EXAMINE existing codebase for similar patterns and interfaces
    - IDENTIFY specific classes, functions, and imports that will be needed
    - FIND integration points with existing modules
    - NOTE database models, API endpoints, or services to interface with
    - CHECK existing error handling and logging patterns

    ### 3. Add comprehensive technical guidance

    Add these sections to the task file:

    **Technical Guidance section:**
    - Key interfaces and integration points in the codebase
    - Specific imports and module references
    - Existing patterns to follow
    - Database models or API contracts to work with
    - Error handling approach used in similar code

    **Implementation Notes section:**
    - Step-by-step implementation approach
    - Key architectural decisions to respect
    - Performance considerations if relevant

    **IMPORTANT:** Do NOT include code examples. Provide structural guidance and references only.

    **IMPORTANT:** Don't create ANY tests. You clearly don't have the context to write consistent and effective tests.

    ### 4. Validate task completeness

    - ENSURE task has clear implementation path
    - VERIFY all integration points are documented
    - CHECK that guidance references actual codebase elements
    - CONFIRM task is self-contained and actionable

    **REPEAT** for every Task

### 5. Update sprint meta with task references

- EDIT sprint meta file to add/update task list
- ORGANIZE tasks by logical grouping or dependency order
- ADD brief description for each task

### 6. Check quality and split high complexity tasks

Review all created tasks for complexity and split any High complexity tasks:

**Complexity Assessment Process:**

- READ each task file completely including description, goals, acceptance criteria, and subtasks
- ASSESS complexity using your judgment about the overall scope and challenge
- CONSIDER the conceptual difficulty, integration challenges, and unknowns
- MARK complexity as Low, Medium, or High in the task frontmatter

**If ANY task is marked as High complexity:**

- SPLIT the task into 2-3 smaller tasks of Low or Medium complexity
- CREATE new task files with proper sequential numbering
- UPDATE the original high-complexity task file or DELETE it
- ENSURE the split tasks together achieve the original goal
- MAINTAIN logical grouping and dependencies

**After all tasks are finalized:**

- VERIFY all tasks are Low or Medium complexity only
- CHECK task numbering is sequential (T01, T02, T03...)
- UPDATE sprint meta file with final task list
- UPDATE project manifest sprint section to reflect actual tasks created

**Output format:**

```markdown
## Sprint Detailed - [YYYY-MM-DD HH:MM]

**Sprint:** [Sprint ID] - [Sprint Name]
**Status:** Planning Complete

**Tasks Created:** [final count after any splits]

- Medium Complexity: [count]
- Low Complexity: [count]

**Task Splitting Summary:**

- [Original T03 split into T03 and T04 due to scope]
- [No other splits needed]

**Final Task List:**

1. T01_S02 - [Title] (Complexity: [Level])
2. T02_S02 - [Title] (Complexity: [Level])
   [Continue for all tasks]

**Next Steps:**

- Review tasks for completeness
- Run `/do_task [FIRST_TASK_IN_SPRINT]` to begin implementation
```
