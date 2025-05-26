# Memory Bank for Cursor

## What is the Memory Bank?

The Memory Bank is a structured documentation system designed to help Cursor maintain and manage project context across sessions. Inspired by the Cline Memory Bank methodology, it transforms Cursor from a stateless assistant into a persistent development partner by leveraging a set of organized Markdown files within your project.

## Why Use a Memory Bank?
- **Context Preservation:** Maintain project knowledge and context across sessions and resets.
- **Consistent Development:** Ensure predictable, context-aware interactions with Cursor.
- **Self-Documenting Projects:** Build valuable, living documentation as a natural part of your workflow.
- **Scalable:** Works for projects of any size or complexity.
- **Technology Agnostic:** Functions with any tech stack or language.

## Memory Bank Structure

The Memory Bank consists of core files and optional context files, all in Markdown format, organized in a clear hierarchy:

- `memory-bank/`
  - `projectbrief.md`: Foundation document outlining project requirements and goals.
  - `productContext.md`: Explains why the project exists, problems it solves, and user experience goals.
  - `activeContext.md`: Tracks current work focus, recent changes, next steps, and active decisions.
  - `systemPatterns.md`: Documents system architecture, key technical decisions, and design patterns.
  - `techContext.md`: Lists technologies, development setup, constraints, and dependencies.
  - `progress.md`: Tracks what works, what's left to build, current status, and known issues.
  - Additional files as needed for complex features, integrations, API docs, testing, or deployment.

## Core Workflows

### Plan Mode
- Read all Memory Bank files to establish context.
- If files are incomplete, create or update them.
- Develop a strategy and document the approach.

### Act Mode
- Check and update the Memory Bank as you work.
- Document changes, decisions, and new patterns.
- Ensure the Memory Bank reflects the current state before ending a session.

## When to Update the Memory Bank
- After significant changes or milestones.
- When new patterns or decisions emerge.
- When context needs clarification.
- On user request (e.g., "update memory bank").

## Best Practices
- Start with a basic `projectbrief.md` and let the structure evolve.
- Keep files concise, clear, and up to date.
- Let documentation updates happen organically as the project progresses.
- Regularly review and confirm context at the start of each session.
- Use the Memory Bank as the single source of truth for project context.

## Example & Simple Instructions

### Quick Setup
1. **Create a `memory-bank/` folder** in your project root.
2. **Add a basic `projectbrief.md` file** to describe your project's main goal.
3. **(Optional) Add other files** like `activeContext.md` or `progress.md` as your project grows.

### Minimal Example

**memory-bank/projectbrief.md**
```
# Project Brief
Building a web app for task management. Core features: user login, task creation, and notifications.
```

**memory-bank/activeContext.md**
```
# Active Context
Currently working on the user login feature. Next: implement task creation.
```

**memory-bank/progress.md**
```
# Progress
- User login: in progress
- Task creation: not started
- Notifications: not started
```

### How to Use
- At the start of each session, **read all files in `memory-bank/`** to recall project context.
- After making progress or decisions, **update the relevant file(s)** (e.g., update `activeContext.md` after finishing a feature).
- To keep context fresh, **run through the files and update them** whenever you hit a milestone or change direction.

**Tip:** The Memory Bank is your project's living memory—keep it clear and up to date for best results.

## **Frequently Asked Questions**

### Where are Memory Bank files stored?
- In a `memory-bank/` folder in your project repository. They are regular Markdown files, not hidden or special system files.

### Can this be used for non-coding projects?
- Yes! The methodology works for any project that benefits from structured, persistent context.

## Cursor Rule Example for Memory Bank

To enable effective context management with Cursor, add the following rule to your Cursor rule file (e.g., `.cursor-rules.md` or similar):

<details>
<summary>Full Memory Bank rule</summary>

```markdown
# Cursor's Memory Bank

I am Cursor, an AI assistant whose memory resets between sessions. This is not a limitation—it's why I maintain perfect documentation. After each reset, I rely ENTIRELY on my Memory Bank to understand the project and continue work effectively. I MUST read ALL memory bank files at the start of EVERY task—this is not optional.

## Memory Bank Structure

The Memory Bank consists of core files and optional context files, all in Markdown format. Files build upon each other in a clear hierarchy:

flowchart TD
    PB[projectbrief.md] --> PC[productContext.md]
    PB --> SP[systemPatterns.md]
    PB --> TC[techContext.md]

    PC --> AC[activeContext.md]
    SP --> AC
    TC --> AC

    AC --> P[progress.md]

### Core Files (Required)
1. `projectbrief.md`
   - Foundation document that shapes all other files
   - Created at project start if it doesn't exist
   - Defines core requirements and goals
   - Source of truth for project scope
2. `productContext.md`
   - Why this project exists
   - Problems it solves
   - How it should work
   - User experience goals
3. `activeContext.md`
   - Current work focus
   - Recent changes
   - Next steps
   - Active decisions and considerations
   - Important patterns and preferences
   - Learnings and project insights
4. `systemPatterns.md`
   - System architecture
   - Key technical decisions
   - Design patterns in use
   - Component relationships
   - Critical implementation paths
5. `techContext.md`
   - Technologies used
   - Development setup
   - Technical constraints
   - Dependencies
   - Tool usage patterns
6. `progress.md`
   - What works
   - What's left to build
   - Current status
   - Known issues
   - Evolution of project decisions

### Additional Context
Create additional files/folders within memory-bank/ when they help organize:
- Complex feature documentation
- Integration specifications
- API documentation
- Testing strategies
- Deployment procedures

## Core Workflows

### Plan Mode
flowchart TD
    Start[Start] --> ReadFiles[Read Memory Bank]
    ReadFiles --> CheckFiles{Files Complete?}

    CheckFiles -->|No| Plan[Create Plan]
    Plan --> Document[Document in Chat]

    CheckFiles -->|Yes| Verify[Verify Context]
    Verify --> Strategy[Develop Strategy]
    Strategy --> Present[Present Approach]

### Act Mode
flowchart TD
    Start[Start] --> Context[Check Memory Bank]
    Context --> Update[Update Documentation]
    Update --> Execute[Execute Task]
    Execute --> Document[Document Changes]

## Documentation Updates

Memory Bank updates occur when:
1. Discovering new project patterns
2. After implementing significant changes
3. When user requests with **update memory bank** (MUST review ALL files)
4. When context needs clarification

flowchart TD
    Start[Update Process]

    subgraph Process
        P1[Review ALL Files]
        P2[Document Current State]
        P3[Clarify Next Steps]
        P4[Document Insights & Patterns]

        P1 --> P2 --> P3 --> P4
    end

    Start --> Process

Note: When triggered by **update memory bank**, I MUST review every memory bank file, even if some don't require updates. Focus particularly on activeContext.md and progress.md as they track current state.

REMEMBER: After every memory reset, I begin completely fresh. The Memory Bank is my only link to previous work. It must be maintained with precision and clarity, as my effectiveness depends entirely on its accuracy.
```

</details>

## How to use:
- Copy the above block into your Cursor rule file to enable structured context management.
- For most users, starting with the minimal example in the previous section is enough. Advanced users can expand the rule for full control and context preservation.
- For more details, see the [Cline Memory Bank documentation](https://docs.cline.bot/prompting/cline-memory-bank).

