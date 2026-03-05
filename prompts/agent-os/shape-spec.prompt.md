---
agent: Plan
description: Gather context and structure a spec/plan for significant work, saved to agent-os/specs/
---

# Shape Spec

Gather context and structure a plan for significant work. Saves a full spec to `agent-os/specs/`.

## Guidelines

- **Offer suggestions** — Present options the user can confirm, adjust, or correct
- **Keep it lightweight** — This is shaping, not exhaustive documentation

## Process

### Step 1: Clarify What We're Building

Ask:
```
What are we building? Please describe the feature or change.
```

Based on their response, ask 1–2 clarifying questions if needed:
- "Is this a new feature or a change to existing functionality?"
- "What's the expected outcome when this is done?"
- "Are there any constraints or requirements I should know about?"

### Step 2: Gather Visuals

Ask:
```
Do you have any visuals to reference? (mockups, wireframes, screenshots, examples from other apps)

Paste images, share file paths, or say "none".
```

Note any visuals provided for inclusion in the spec folder.

### Step 3: Identify Reference Implementations

Ask:
```
Is there similar code in this codebase I should reference?

Examples:
- "The comments feature is similar to what we're building"
- "Look at how src/features/notifications/ handles real-time updates"
- "No existing references"
```

If references are provided, read and analyze them to inform the plan.

### Step 4: Check Product Context

Check if `agent-os/product/` exists and contains files.

If it exists, read the key files and ask:
```
I found product context in agent-os/product/. Should this feature align with any specific product goals or constraints?

Key points from your product docs:
- [summarize relevant points]

(Confirm alignment or note any adjustments)
```

If no product folder exists, skip this step.

### Step 5: Surface Relevant Standards

Read `agent-os/standards/index.yml` to identify relevant standards based on the feature being built.

Ask to confirm:
```
Based on what we're building, these standards may apply:

1. **[folder/file]** — [description]
2. **[folder/file]** — [description]

Should I include these in the spec? (yes / adjust: remove 2, add [other])
```

Read the confirmed standards files and include their content in the plan context.

### Step 6: Generate Spec Folder Name

Create a folder name using this format:
```
YYYY-MM-DD-HHMM-{feature-slug}/
```

Where:
- Date/time is current timestamp
- Feature slug is derived from the feature description (lowercase, hyphens, max 40 chars)

Example: `2026-01-15-1430-user-comment-system/`

Create `agent-os/specs/` if it doesn't exist.

### Step 7: Structure the Plan

Present this structure for user confirmation:

```
Here's the plan structure. Task 1 saves all shaping work before implementation begins.

---

## Task 1: Save Spec Documentation

Create `agent-os/specs/{folder-name}/` with:
- plan.md — This full plan
- shape.md — Shaping notes (scope, decisions, context)
- standards.md — Relevant standards that apply
- references.md — Pointers to reference implementations studied
- visuals/ — Any mockups or screenshots provided

## Task 2: [First implementation task]

[Description]

## Task 3: [Next task]

...

---

Does this plan structure look right?
```

### Step 8: Complete the Plan

Build out the remaining implementation tasks based on:
- Feature scope from Step 1
- Patterns from reference implementations (Step 3)
- Constraints from standards (Step 5)

Each task should be specific and actionable.

### Step 9: Ready for Execution

```
Plan complete.

1. Task 1 will save all spec documentation first
2. Then implementation tasks will proceed

Ready to start? (approve / adjust)
```

## Output Structure

```
agent-os/specs/{YYYY-MM-DD-HHMM-feature-slug}/
├── plan.md           # The full plan
├── shape.md          # Shaping decisions and context
├── standards.md      # Which standards apply and key points
├── references.md     # Pointers to similar code
└── visuals/          # Mockups, screenshots (if any)
```

## File Contents

### shape.md

```markdown
# {Feature Name} — Shaping Notes

## Scope
[What we're building]

## Decisions
- [Key decisions made during shaping]
- [Constraints or requirements noted]

## Context
- **Visuals:** [List of visuals, or "None"]
- **References:** [Code references studied]
- **Product alignment:** [Notes from product context, or "N/A"]

## Standards Applied
- [folder/file] — [why it applies]
```

### standards.md

```markdown
# Standards for {Feature Name}

The following standards apply to this work.

---

## [folder/file]

[Full content of the standard file]
```

### references.md

```markdown
# References for {Feature Name}

## Similar Implementations

### {Reference name}
- **Location:** `[path]`
- **Relevance:** [Why this is relevant]
- **Key patterns:** [What to borrow from this]
```

## Tips

- **Keep shaping fast** — Capture enough to start, refine as you build
- **Visuals are optional** — Not every feature needs mockups
- **Standards guide, not dictate** — They inform the plan but aren't always mandatory
- **Specs are discoverable** — Months later, someone can find this spec and understand what was built and why
