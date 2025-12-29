# Enhance Plugin

Prompt enhancement plugin that transforms vague user prompts into clear, structured, and actionable specifications.

## Structure

```
enhance-plugin/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata
├── README.md                  # This file
├── commands/
│   └── enhance.md            # /enhance slash command
└── skills/
    └── enhance/
        ├── SKILL.md           # Skill definition (auto-triggered)
        ├── examples/
        │   └── prompt-examples.md    # Enhancement examples
        └── references/
            └── enhancement-guide.md  # Enhancement principles
```

## Features

This plugin provides the `/enhance` command that:

- Transforms vague prompts into specific, actionable specifications
- Adds missing technical details and context
- Defines verifiable completion criteria
- Follows the SMART principle (Specific, Measurable, Achievable, Relevant, Testable)

## Usage

Invoke the skill by typing:

```
/enhance Build a todo API and make it good
```

The skill will output:
1. The original prompt
2. An enhanced version with clear structure
3. Improvement notes explaining what was enhanced
4. A confirmation prompt

## Enhancement Categories

The skill handles various prompt types:

- **New Feature Development**: Defines scope, data models, API design
- **Bug Fixes**: Adds reproduction steps, expected behavior, verification methods
- **Performance Optimization**: Sets measurable targets and analysis steps
- **Code Refactoring**: Limits scope, ensures behavior preservation

## Reference Materials

- [prompt-examples.md](skills/enhance/examples/prompt-examples.md) - Comprehensive examples
- [enhancement-guide.md](skills/enhance/references/enhancement-guide.md) - Principles and techniques
