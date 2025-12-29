---
description: Enhance and optimize user prompts into clear, structured, actionable specifications
argument-hint: <your prompt to enhance>
allowed-tools: [Read]
---

# Prompt Enhancement Command

The user submitted a raw prompt via `/enhance` command. Your task is to **immediately generate an enhanced version**.

## What You Must Do

1. Read the original prompt from $ARGUMENTS
2. Output the enhanced version in the format below
3. Ask the user to confirm

## Output Format (Strictly Follow)

```
### Original Prompt
> [Copy content from $ARGUMENTS]

---

### Enhanced Prompt

## Task Description
[One sentence clearly describing what needs to be done]

## Technical Requirements
- [Specific tech stack/framework]
- [Other technical constraints]

## Implementation Details
- [Feature point 1]
- [Feature point 2]
- [Edge cases]

## Completion Criteria
- [ ] [Verifiable criterion 1]
- [ ] [Verifiable criterion 2]
- [ ] [Testing/documentation requirements]

---

### Improvement Notes
1. [What improvement you made]
2. [What improvement you made]

---

Confirm this enhanced version? Once confirmed, I will execute accordingly.
```

## Enhancement Principles

- Transform vague words (like "make it good") into specific criteria
- Add missing technical details
- Add verifiable completion criteria
- If information is insufficient, add a "Needs Clarification" section

## Category-Specific Guidelines

### New Feature Development
Focus on: scope, data models, API design, UI/UX specs, testing strategy

### Bug Fixes
Focus on: reproduction steps, expected vs actual behavior, impact scope, verification method

### Performance Optimization
Focus on: current baseline, target metrics, acceptable trade-offs, measurement methods

### Code Refactoring
Focus on: scope limits, behavior preservation, quality metrics, test coverage

## Example

**$ARGUMENTS**: Build a todo API and make it good.

**Your output**:

### Original Prompt
> Build a todo API and make it good.

---

### Enhanced Prompt

## Task Description
Build a fully functional RESTful Todo API

## Technical Requirements
- Use the project's existing tech stack
- Follow RESTful design standards

## Implementation Details
- CRUD endpoints: GET/POST/PUT/DELETE /api/todos
- Data model: id, title, completed, createdAt, updatedAt
- Input validation: title required, length limits
- Error handling: unified error response format

## Completion Criteria
- [ ] All CRUD endpoints work correctly
- [ ] Input validation implemented
- [ ] Basic tests included
- [ ] API documentation complete

---

### Improvement Notes
1. Transformed "make it good" into specific completion criteria
2. Defined CRUD endpoint design
3. Added data model definition
4. Added testing and documentation requirements

---

Confirm this enhanced version? Once confirmed, I will execute accordingly.
