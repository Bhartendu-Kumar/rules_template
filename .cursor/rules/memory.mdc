---
description: ALWAYS INCLUDE to HAVE Project Context
globs: 
alwaysApply: false
---
---
description: ALWAYS INCLUDE to HAVE Project Context.
globs: 
alwaysApply: true
---
# Memory Files Structure
This outlines the fundamental principles, required files, workflow structure, and essential procedures that govern documentation, and maintaining a memory using file system.
The Memory Files consists of required core files and optional context files. Files build upon each other in a clear hierarchy:
```mermaid
flowchart TD
    PB[ [product_requirement_docs.md](mdc:docs/product_requirement_docs.md) ] --> PC[ [technical.md](mdc:docs/technical.md) ]
    PB --> SP[ [architecture.md](mdc:docs/architecture.md) ]

    SP --> TC[ [tasks_plan.md](mdc:tasks/tasks_plan.md) ]
    PC --> TC
    PB --> TC
    
    TC --> AC[ [active_context.md](mdc:tasks/active_context.md) ]

    AC --> ER[ [error-documentation.mdc](mdc:.cursor/rules/error-documentation.mdc)]
    AC --> LL[ [lessons-learned.mdc](mdc:.cursor/rules/lessons-learned.mdc) ]
    
    subgraph LIT[ @docs/literature ]
        L1[...]
        L2[...]
    end
    
    subgraph RFC[ @tasks/rfc/ ]
        R1[...]
        R2[...]
    end
    
    PC --o LIT
    TC --o RFC

```
## Core Files (Required)
  7 files: 
  1. [product_requirement_docs.md](mdc:docs/product_requirement_docs.md) (docs/product_requirement_docs.md): Product Requirement Document (PRD) for the project or an SOP. 
  - Why this project exists
  - Problems it solves
  - Defines core requirements and goals
  - Foundation document that shapes all other files
  - Source of truth for project scope
  - Created at project start if it doesn't exist

  2. [architecture.md](mdc:docs/architecture.md) (docs/architecture.md): System architecture
  - How it should work
  - Component relationships
  - Dependencies
  - Work flow of the Solution
  - Mermaid diagram of solution overview: each component and code flow

  3. [technical.md](mdc:docs/technical.md) (docs/technical.md): Development environment and stack
  - Technologies used
  - Development setup
  - Key technical decisions
  - Design patterns in use
  - Technical constraints

  4. [tasks_plan.md](mdc:tasks/tasks_plan.md) (tasks/tasks_plan.md): Detailed Task backlog
  - In-Depth Tasks list and Project Progress
  - What works
  - What's left to build
  - Current status
  - Known issues
  
  5. [active_context.md](mdc:tasks/active_context.md) (tasks/active_context.md): Current state of development
  - Current work focus
  - Active decisions and considerations
  - Recent changes
  - Next steps

  6. [error-documentation.mdc](mdc:.cursor/rules/error-documentation.mdc) (.cursor/rules/error-documentation.mdc): 
  - During your interaction, if you find a fix to a mistake in this project or a correction you received reusable, you should take note in the @error-documentation.mdc file so you will not make the same mistake again.
  - Known issues: their state, context, and resolution

  7. [lessons-learned.mdc](mdc:.cursor/rules/lessons-learned.mdc) (.cursor/rules/lessons-learned.mdc): learning journal for each project
  - It captures important patterns, preferences, and project intelligence
  - It is detailed in @lessons-learned.mdc

## Context Files (Optional)
Detailed docs. Retrieve on demand if needed for context.

1. docs/literature/ :
  - literature survey and researches are in this directory  
  - Each literature topic is a latex file (docs/literature/*.tex)

2. tasks/rfc/ :
  - contains RFC for each individual task in @tasks_plan.md
  - RFCs will be in latex file format (tasks/*.tex)

## Additional Context
Create additional files or folders as Memory files in docs/ or tasks/ when they help organize:
- Integration specifications
- Testing strategies
- Benchmarking setups
- Possible Extensions
- Deployment procedures

# Core Workflows
Now we define the procedural workflows to read/write to these memeory files.
The system operates in distinct MODES: (PLAN/ACT) or analogously (Architect/Code), controlled exclusively by the user input or the task in current request. Current input will determine the MODE, based on which the Workflow selection is always dictated. In user input explicit mode setting can also be specified by "MODE = PLAN MODE"/"Architect MODE" or "MODE = ACT MODE"/"Code MODE", so if explicit MODE setting present follow that, else guess the mode from the request. Ask for the MODE if you are not 100% confident, if any doubt ask explicitely.

## PLAN or Architect MODE
```mermaid
flowchart TD
    Start[Start] --> ReadFiles[Read Memory Files ("docs/": (a)"docs/architecture.md" (b)"docs/product_requirement_docs.md" (c)"docs/technical.md". "tasks/" : (a)"tasks/active_context.md" (b)"tasks/tasks_plan.md". if needed further: "docs/literature" and "tasks/rfc") ]
    ReadFiles --> CheckFiles{Files Complete?}
    
    CheckFiles -->|No| Plan[Create Plan]
    Plan --> DocumentChat[Document in Chat]
    
    CheckFiles -->|Yes| VerifyContext[Verify Context]
    VerifyContext --> Strategy[Develop Strategy]
    Strategy --> Present[Present Approach]
    
    Present --> Verification{Approach Verified?}

    Verification -->|No| Clarify[Seek Clarification]
    Clarify --> Strategy[Develop Strategy]

    Verification -->|Yes| DocumentMemory[Document in Memory Files ("docs/": (a)"docs/architecture.md" (b)"docs/product_requirement_docs.md" (c)"docs/technical.md". "tasks/" : (a)"tasks/active_context.md" (b)"tasks/tasks_plan.md" if needed further: "docs/literature" and "tasks/rfc")]
```

## ACT or Code MODE
```mermaid
flowchart TD
    Start[Start] --> Context[Check Memory Files (Core Files always ("docs/": (a)"docs/architecture.md" (b)"docs/product_requirement_docs.md" (c)"docs/technical.md". "tasks/" : (a)"tasks/active_context.md" (b)"tasks/tasks_plan.md"), rest based on context (if needed further: "docs/literature" and "tasks/rfc")) ]
    Context --> Update[Update Documentation]
    Update --> Rules[Update [lessons-learned.mdc](mdc:.cursor/rules/lessons-learned.mdc), [error-documentation.mdc](mdc:.cursor/rules/error-documentation.mdc) if needed]
    Rules --> Execute[Execute Task]
    Execute --> Document[Document Changes in Memory Files ("docs/": (a)"docs/architecture.md" (b)"docs/product_requirement_docs.md" (c)"docs/technical.md". "tasks/" : (a)"tasks/active_context.md" (b)"tasks/tasks_plan.md" if needed further: "docs/literature" and "tasks/rfc") ]
```

# Documentation Updates

Memory Files updates occur when:
1. Discovering new project patterns
2. After implementing significant changes
3. When user requests with **update memory files** (MUST review ALL Core Files)
4. When context needs clarification
5. After significant part of Plan is verified

```mermaid
flowchart TD
    Start[Update Process]
    
    subgraph Process
        P1[Review Core Files]
        P2[Document Current State in [active_context.md](mdc:tasks/active_context.md) and [tasks_plan.md](mdc:tasks/tasks_plan.md) ]
        P3[Clarify Next Steps and document in [tasks_plan.md](mdc:tasks/tasks_plan.md) ]
        P4[Update [lessons-learned.mdc](mdc:.cursor/rules/lessons-learned.mdc), [error-documentation.mdc](mdc:.cursor/rules/error-documentation.mdc)]
        P5 Update [ [architecture.md](mdc:docs/architecture.md) ]
        
        P1 --> P2 --> P3 --> P4
    end
    
    Start --> Process
```

Note: When triggered by **update memory files**, I MUST review every Core memory  file, even if some don't require updates. Focus particularly on [active_context.md](mdc:tasks/active_context.md) and [tasks_plan.md](mdc:tasks/tasks_plan.md) as they track current state. And [architecture.md](mdc:docs/architecture.md) has a section of current workflow that also gets updated by any code updates.

# Project Intelligence ( [lessons-learned.mdc](mdc:.cursor/rules/lessons-learned.mdc) [.cursor/rules/lessons-learned.mdc] )

The [lessons-learned.mdc](mdc:.cursor/rules/lessons-learned.mdc) file is my learning journal for each project. It captures important patterns, preferences, and project intelligence that help me work more effectively. As I work with you and the project, I'll discover and document key insights that aren't obvious from the code alone.

```mermaid
flowchart TD
    Start{Discover New Pattern}
    
    subgraph Learn [Learning Process]
        D1[Identify Pattern]
        D2[Validate with User]
        D3[Document in [lessons-learned.mdc](mdc:.cursor/rules/lessons-learned.mdc) ]
    end
    
    subgraph Apply [Usage]
        A1[Read [lessons-learned.mdc](mdc:.cursor/rules/lessons-learned.mdc) ]
        A2[Apply Learned Patterns]
        A3[Improve Future Work]
    end
    
    Start --> Learn
    Learn --> Apply
```

## What to Capture
- Critical implementation paths
- User preferences and workflow
- Project-specific patterns
- Known challenges
- Evolution of project decisions
- Tool usage patterns

The format is flexible - focus on capturing valuable insights that help me work more effectively with you and the project. Think of [lessons-learned.mdc](mdc:.cursor/rules/lessons-learned.mdc) as a living document that grows smarter as we work together.
