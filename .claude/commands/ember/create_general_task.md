# Create General Task - Execute top to bottom

Creates a new general task in `.ember/04_GENERAL_TASKS/` following project documentation standards.

## Create a TODO with EXACTLY these 6 Items

1. Parse task arguments and determine task ID
2. Load project context and documentation requirements
3. Research codebase for implementation context
4. Create and populate task file with technical guidance
5. Update project manifest
6. Perform final quality check and report

## DETAILS on every TODO item

### 1. Parse task arguments and determine task ID

The argument format is: `<Task Title or Description>`

- If $ARGUMENTS are empty, prompt user for task details
- Generate sequential task ID by examining existing tasks in `.ember/04_GENERAL_TASKS/`
- Find highest task number (T###) and increment by 1
- Format: `T###_<Task_Title_Snake_Case>.md`
- **IMPORTANT:** Task IDs must be sequential with no gaps

### 2. Load project context and documentation requirements

Use PARALLEL SUBAGENTS to READ and UNDERSTAND the project's context:

- READ `.ember/00_PROJECT_MANIFEST.md` - Get current project state
- READ `.ember/01_PROJECT_DOCS/ARCHITECTURE.md` - Understand system constraints
- **IMPORTANT:** General tasks must align with documented architecture

### 3. Research codebase for implementation context

Based on the task description, use PARALLEL SUBAGENTS to:

- SEARCH for existing patterns similar to what the task requires
- IDENTIFY key interfaces, classes, or modules that will be affected
- FIND examples of similar implementations in the codebase
- LOCATE relevant test patterns and existing test files
- DISCOVER error handling and logging patterns used
- MAP OUT integration points with existing code
- **DOCUMENT** all findings for inclusion in task

### 4. Create and populate task file with technical guidance

**CREATE** task file using `.ember/99_TEMPLATES/task_template.md`:

- Copy template structure exactly to `.ember/04_GENERAL_TASKS/T###_<Title>.md`
- Include timestamp: Execute `date '+%Y-%m-%d %H:%M:%S'` for creation time

**POPULATE** with comprehensive details:

- **Title**: Clear, actionable task name
- **Context**: Link to architecture docs and project state
- **Requirements**: Specific, measurable outcomes
- **Acceptance Criteria**: Clear definition of done
- **Dependencies**: Reference relevant sprints/milestones
- **Technical Guidance**: Key interfaces, integration points, existing patterns to follow (with file references)
- **Implementation Notes**: Step-by-step approach, architectural decisions to respect, specific files to modify, testing patterns
- **IMPORTANT:** Do NOT include code examples. Provide structural guidance and file references only.

### 5. Update project manifest

**UPDATE** `.ember/00_PROJECT_MANIFEST.md`:

- Add task to "## General Tasks" section
- Format: `- [ ] T###: [Task Title] - Status: Not Started`
- Maintain alphabetical/numerical ordering
- Link to task file: `[T###](04_GENERAL_TASKS/T###_Title.md)`
- **IMPORTANT:** Preserve all existing content

### 6. Perform final quality check and report

**QUALITY CHECK**:

- Task file follows template completely
- All sections properly filled including technical guidance
- References to documentation and codebase are valid
- Task ID is sequential and unique
- Manifest updated correctly
- Technical guidance references actual files and patterns
- No scope creep or architecture violations

**OUTPUT FORMAT**:

```markdown
✅ **Created**: T###\_<Title>.md
📋 **Type**: General Task
🎯 **Purpose**: [One-line summary]
📚 **References**: [Key documentation links]
🔧 **Key Integration Points**: [Main files/modules to modify]
🧪 **Test Approach**: [Testing pattern to follow]
⏭️ **Next Step**: Review task details and run `/do_task T###` to begin
```
