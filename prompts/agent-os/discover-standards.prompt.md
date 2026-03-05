---
agent: agent
description: Extract tribal knowledge from your codebase into concise, documented standards in agent-os/standards/
---

# Discover Standards

Extract tribal knowledge from your codebase into concise, documented standards.

## Guidelines

- **Write concise standards** — Use minimal words. Standards must be scannable by AI agents without bloating context windows.
- **Offer suggestions** — Present options the user can confirm, choose between, or correct.

## Process

### Step 1: Determine Focus Area

Check if the user specified an area when running this prompt. If they did, skip to Step 2.

If no area was specified:

1. Analyze the codebase structure (folders, file types, patterns)
2. Identify 3-5 major areas. Examples:
   - **Backend areas:** API routes, database/models, authentication, background jobs
   - **Cross-cutting:** Error handling, validation, testing, naming conventions, file structure
3. Ask the user:

```
I've identified these areas in your codebase:

1. **[Area 1]** ([path]) — [brief description]
2. **[Area 2]** ([path]) — [brief description]
...

Which area should we focus on for discovering standards? (Pick one, or suggest a different area)
```

Wait for user response before proceeding.

### Step 2: Analyze & Present Findings

Once an area is determined:

1. Read 5–10 representative files in that area
2. Look for patterns that are:
   - **Unusual or unconventional** — Not standard framework/library patterns
   - **Opinionated** — Specific choices that could have gone differently
   - **Tribal** — Things a new developer wouldn't know without being told
   - **Consistent** — Patterns repeated across multiple files

3. Present findings and let the user select:

```
I analyzed [area] and found these potential standards worth documenting:

1. **[Pattern Name]** — [one-line description]
2. **[Pattern Name]** — [one-line description]
3. **[Pattern Name]** — [one-line description]

Which would you like to document? (e.g. "Yes, all", "Just 1 and 3", "Add: [your suggestion]", "Skip")
```

Wait for user selection before proceeding.

### Step 3: Ask Why, Then Draft Each Standard

For each selected standard, complete this full loop before moving to the next:

1. Ask 1–2 clarifying questions about the "why" behind the pattern:
   - "What problem does this pattern solve? Why not use the default/common approach?"
   - "Are there exceptions where this pattern shouldn't be used?"
   - "What's the most common mistake a developer or AI agent makes with this?"
2. Wait for user response
3. Draft the standard incorporating their answer
4. Confirm with user before creating the file
5. Create the file if approved

**Do NOT batch all questions upfront.** Process one standard at a time.

### Step 4: Create the Standard File

For each standard (after completing Step 3's Q&A):

1. Determine the appropriate folder (create if needed):
   - `api/`, `database/`, `backend/`, `testing/`, `global/`, etc.
2. Check if a related standard file already exists — append to it if so
3. Draft the content and confirm:

```
Here's the draft for [folder]/[filename].md:

---
[draft content]
---

Create this file? (yes / edit: [your changes] / skip)
```

4. Create or update the file in `agent-os/standards/[folder]/`
5. Repeat Steps 3–4 for the next selected standard

### Step 5: Update the Index

After all standards are created:

1. Scan `agent-os/standards/` for all `.md` files
2. For each new file without an index entry, propose a description:

```
New standard needs an index entry:
  File: [folder]/[filename].md

Suggested description: "[one-sentence description]"

Accept? (yes / or type a better description)
```

3. Update `agent-os/standards/index.yml` — alphabetize by folder, then filename.

### Step 6: Offer to Continue

```
Standards created for [area]:
- [folder]/[file].md
- ...

Would you like to discover standards in another area, or are we done?
```

## Output Location

All standards: `agent-os/standards/[folder]/[standard].md`  
Index file: `agent-os/standards/index.yml`

## Writing Concise Standards

Standards are injected into AI context windows — every word costs tokens.

- **Lead with the rule** — State what to do first, explain why second
- **Use code examples** — Show, don't tell
- **Skip the obvious** — Don't document what the code already makes clear
- **One standard per concept** — Don't combine unrelated patterns
- **Bullet points over paragraphs** — Scannable beats readable
