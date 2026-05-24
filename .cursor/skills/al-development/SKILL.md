---
name: al-development
description: >-
  Develops Microsoft Dynamics 365 Business Central extensions in AL following
  Microsoft AL Guidelines. Use when writing, reviewing, or refactoring AL code,
  .al files, app.json, BC extensions, tables, pages, codeunits, reports,
  event subscribers, or Business Central development.
---

# AL Development

Guidance from [Microsoft AL Guidelines Vibe Coding Rules](https://github.com/microsoft/alguidelines/tree/main/content/docs/agentic-coding/vibe-coding-rules).

## Before Writing Code

1. Read `app.json` for platform/application version and `idRange`
2. Assign object IDs only within the configured range
3. Prefer extensions over modifying standard BC objects

## Core Principles

- Event-driven extensibility; never modify standard application objects
- Integration events and page/table extensions over base object changes
- 2-space indentation, PascalCase for variables, procedures, and object names
- File naming: `ObjectName.ObjectType.al` (e.g., `CustomerCard.Page.al`)
- Object names max 30 characters (26 for the name itself)
- XML documentation on public codeunit procedures
- Only generate test code when explicitly requested
- In AL-Go workspaces: app logic in App project, tests in Test project

## Performance

- Filter with `SetRange`/`SetFilter` before `FindSet`/`Get`
- Call `SetLoadFields` before the find/get, not after
- Prefer `CalcSums`/`CalcFields` over manual aggregation loops
- Use temporary tables, dictionaries, and lists for in-memory processing

## Error Handling

- Use `[TryFunction]` for operations that may fail
- All user-facing messages via `Label` variables with translator comments
- Never hardcode error strings

## Events

- Descriptive parameter names in event subscribers (not generic `Rec`)
- Prefer integration events for extensibility

## Response Style

- Concise, actionable advice with specific AL method references
- Explain reasoning behind recommendations
- Focus on practical implementation

## Additional Resources

- Detailed naming, performance, and error-handling examples: [reference.md](reference.md)
- [BC Developer Reference](https://learn.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-reference-overview)
- [AL Guidelines repository](https://github.com/microsoft/alguidelines)
