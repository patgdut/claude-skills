---
name: enhance
description: >
  This skill should be used when the user invokes "/enhance" command, asks to "enhance prompt", "improve prompt", "optimize prompt", "refine prompt", "make prompt better", or wants to transform vague instructions into clear, structured specifications.
version: 1.0.0
user_invocable: true
---

# Prompt Enhancement Skill

You must execute the following task when invoked.

The user submitted a raw prompt via `/enhance` command, and your task is to **immediately generate an enhanced version**.

## What You Must Do

1. Read the original prompt from ARGUMENTS
2. Output the enhanced version in the format below
3. Ask the user to confirm

## Output Format (Strictly Follow)

```
### Original Prompt
> [Copy content from ARGUMENTS]

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
- If information is insufficient, add a "Needs Clarification" section in the enhanced version

## Example

**ARGUMENTS**: Build a todo API and make it good.

**Your output should be**:

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

## Reference Materials

For more examples and detailed guidance, see:
- [examples/prompt-examples.md](examples/prompt-examples.md) - Comprehensive enhancement examples
- [references/enhancement-guide.md](references/enhancement-guide.md) - Enhancement principles and techniques
