---
agent: agent
description: Establish foundational product documentation (mission, roadmap, tech stack) in agent-os/product/
---

# Plan Product

Establish foundational product documentation through an interactive conversation. Creates `mission.md`, `roadmap.md`, and `tech-stack.md` in `agent-os/product/`.

## Guidelines

- **Keep it lightweight** — gather enough to create useful docs without over-documenting
- **One question at a time** — don't overwhelm with multiple questions at once

## Process

### Step 1: Check for Existing Product Docs

Check if `agent-os/product/` exists and contains any of these files:
- `mission.md`
- `roadmap.md`
- `tech-stack.md`

**If any files exist**, ask:

```
I found existing product documentation:
- mission.md: [exists/missing]
- roadmap.md: [exists/missing]
- tech-stack.md: [exists/missing]

Would you like to:
1. Start fresh (replace all)
2. Update specific files
3. Cancel
```

If option 2, ask which files to update and only gather info for those.  
If option 3, stop here.

**If no files exist**, proceed to Step 2.

### Step 2: Gather Product Vision (for mission.md)

Ask:
```
Let's define your product's mission.

What problem does this product solve?
```

After they respond, ask:
```
Who is this product for? (Describe target users or audience)
```

After they respond, ask:
```
What makes your solution unique? (Key differentiator or approach)
```

### Step 3: Gather Roadmap (for roadmap.md)

Ask:
```
What are the must-have features for launch (MVP)?
```

After they respond, ask:
```
What features are planned for after launch? (or "none yet")
```

### Step 4: Establish Tech Stack (for tech-stack.md)

First, check if `agent-os/standards/global/tech-stack.md` exists.

**If found**, read it and ask:
```
I found a tech stack standard in your standards:

[Summary of key technologies from global/tech-stack.md]

Does this project use the same tech stack, or does it differ?

1. Same as standard (use as-is)
2. Different (I'll specify)
```

**If not found (or option 2 above)**, ask:
```
What technologies does this project use?

- Frontend: (e.g. React, Vue, N/A)
- Backend: (e.g. Rails, Node, Rust, N/A)
- Database: (e.g. PostgreSQL, MongoDB, N/A)
- Other: (hosting, external APIs, key tools)
```

### Step 5: Generate Files

Create the `agent-os/product/` directory if needed. Generate each file:

#### mission.md

```markdown
# Product Mission

## Problem

[What problem this product solves]

## Target Users

[Who this product is for]

## Solution

[What makes the solution unique]
```

#### roadmap.md

```markdown
# Product Roadmap

## Phase 1: MVP

[Must-have features for launch]

## Phase 2: Post-Launch

[Planned future features, or "To be determined"]
```

#### tech-stack.md

```markdown
# Tech Stack

## Frontend

[Frontend technologies, or "N/A"]

## Backend

[Backend technologies, or "N/A"]

## Database

[Database, or "N/A"]

## Other

[Other tools, hosting, services — omit if nothing to add]
```

### Step 6: Confirm Completion

```
Product documentation created:

  agent-os/product/mission.md
  agent-os/product/roadmap.md
  agent-os/product/tech-stack.md

Review these files and edit directly, or re-run this prompt to update them.
```

## Tips

- Brief answers are fine — these docs can be expanded later
- Use placeholder "To be defined" if the user wants to skip a section
- The shape-spec prompt reads these files when planning features
