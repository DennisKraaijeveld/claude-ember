# Code Review - Execute top to bottom

Use the following instructions from top to bottom to execute a Code Review.

## Create a TODO with EXACTLY these 6 Items

1. Analyze the Scope given
2. Find code changes within Scope
3. Find relevant Specification and Documentation
4. Compare code changes against Documentation and Requirements
5. Analyze possible differences
6. Provide PASS/FAIL verdict with details

Follow step by step and adhere closely to the following instructions for each step.

## DETAILS on every TODO item

### 1. Analyze the Scope given

check: <$ARGUMENTS>

If empty, use default, otherwise interpret <$ARGUMENTS> to identify the scope of the Review. Only continue if you can find meaningful changes to review.

**CONTEXT:** Before reviewing code changes:

- Read `.ember/00_PROJECT_MANIFEST.md` to understand current sprint and milestone context
- Use the manifest to identify which sprint is active and what work is in scope
- Only evaluate against requirements appropriate for the current sprint's deliverables
- If scope unclear, request clarification before proceeding

### 2. Find code changes within Scope

With the identified Scope use `git diff` (on default: `git diff HEAD~1`) to find code changes.

- If no meaningful changes found, EXIT with "No changes to review"

### 3. Find relevant Specifications and Documentation

- FIND the Task, Sprint and Milestone involved in the work that was done and output your findings
- Navigate to `.ember/03_SPRINTS/` to find the current sprint directory
- READ the sprint meta file to understand sprint objectives and deliverables FIRST (highest priority)
- If a specific task is in scope, find and READ the task file in the sprint directory
- IDENTIFY related requirements in `.ember/02_REQUIREMENTS/` for the current milestone
- READ only RELEVANT Documents especially in `.ember/01_PROJECT_DOCS/` and `.ember/02_REQUIREMENTS/`
- **IMPORTANT:** Focus on current sprint deliverables, not future milestone features

### 4. Compare code changes against Documentation and Requirements

**ZEN-ONLY CODE REVIEW:**

- Use the `zen:review` mcp tool to perform comprehensive code analysis.
- Pass all relevant files identified in the code changes to the zen code review tool.
- Ensure the zen review checks for strict compliance with all found Requirements, Specs, and Documentation:
  - **Data models / schemas** — fields, types, constraints, relationships.
  - **APIs / interfaces** — endpoints, params, return shapes, status codes, errors.
  - **Config / environment** — keys, defaults, required/optional.
  - **Behaviour** — business rules, side-effects, error handling.
  - **Quality** — naming, formatting, tests, linter status.
- Deviations from the Specs are not allowed. Be extremely strict.
- If zen review finds any issues, call a **FAIL** and ask the User.
- Zero tolerance for not following the Specs and Documentation.

### 5. Analyze the differences

**ANALYZE ZEN CODE REVIEW RESULTS:**

- Analyze zen code review results and categorize findings by severity
- Consolidate all issues found from zen review
- Give every issue a Severity Score based on zen classification:
  - **Critical (9-10)**: Security vulnerabilities, data corruption risks, spec violations
  - **High (7-8)**: Logic errors, API contract violations, major requirement deviations
  - **Medium (5-6)**: Code quality issues, minor spec deviations, maintainability concerns
  - **Low (1-4)**: Style issues, documentation gaps, optimization opportunities
- Remember consolidated list of issues and scores for output

- **PRIORITIZE** zen-identified critical and high severity issues

### 6. Provide PASS/FAIL verdict with details

- Call a **FAIL** on any differences found.
  - Zero Tolerance - even on well meant additions.
  - Leave it on the user to decide if small changes are allowed.
- Only **PASS** if no discrepancy appeared.

#### IMPORTANT: Output Format

- Output the results of your review to the task's **## Output Log** section in the task file
- Find the task file in `.ember/03_SPRINTS/` or `.ember/04_GENERAL_TASKS/` based on the scope
- Append the review results to the existing Output Log with timestamp
- Output Format:
  ```
  [YYYY-MM-DD HH:MM]: Code Review - PASS/FAIL (Enhanced with Zen Analysis)
  Result: **FAIL/PASS** Your final decision on if it's a PASS or a FAIL.
  **Scope:** Inform the user about the review scope.
  **Zen Analysis:** Summary of zen code review findings and overall assessment.
  **Manual Validation:** Results of manual specification compliance check.
  **Consolidated Findings:** Detailed list with all Issues found and Severity Score (Critical/High/Medium/Low).
  **Summary:** Short summary on what is wrong or not.
  **Recommendation:** Your personal recommendation on further steps.
  ```
- Also output a brief result summary to the console for immediate feedback
