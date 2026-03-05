---
agent: agent
description: Inject relevant standards from agent-os/standards/ into the current context
---

# Inject Standards

Inject relevant standards into the current context.

## Usage

Run this prompt with or without arguments:

- **No arguments** — Analyze context and suggest relevant standards
- **With arguments** — Directly inject specific standards:
  - `inject-standards api` — All standards in `api/`
  - `inject-standards api/response-format` — Single file
  - `inject-standards api/response-format api/auth` — Multiple files
  - `inject-standards root` — All standards directly in `agent-os/standards/`
  - `inject-standards root/naming` — Single root-level file

**Note:** `root` refers to `.md` files directly in `agent-os/standards/` (not in a subfolder).

## Process

### Step 1: Detect Context Scenario

Determine which scenario applies:

1. **Conversation** — Regular chat, implementing code, answering questions
2. **Building a Prompt/Skill** — Creating a reusable `.github/prompts/` or skill file
3. **Planning/Spec** — Building a spec or plan for a feature

If it's not obvious, ask:

```
I'll inject the relevant standards. How should I format them?

1. **Conversation** — Read standards into our chat (for implementation work)
2. **Prompt/Skill** — Output file references to include in a prompt you're building
3. **Plan** — Output file references to include in a plan/spec

Which scenario? (1, 2, or 3)
```

### Step 2: Read the Index (Auto-Suggest Mode)

Read #file:agent-os/standards/index.yml to get available standards and their descriptions.

If not found:
```
No standards index found. Run the discover-standards or index-standards prompt first.
```

### Step 3: Analyze Work Context

Look at the current conversation to understand what the user is working on: type of work, technologies, goal.

### Step 4: Match and Suggest

Match index descriptions against the context and present suggestions:

```
Based on your task, these standards may be relevant:

1. **[folder/file]** — [description]
2. **[folder/file]** — [description]
3. **[folder/file]** — [description]

Inject these? (yes / just 1 and 3 / add: [folder/file] / none)
```

Keep suggestions focused (2–5 standards typically).

### Step 5: Inject Based on Scenario

---

#### Scenario: Conversation

Read the standards files and present them:

```
I've read the following standards as relevant to what we're working on:

--- Standard: [folder/file] ---

[full content]

--- End Standard ---

**Key points:**
- [bullet summary]
```

---

#### Scenario: Building a Prompt/Skill

Ask how to include them:

```
How should these standards be included in your prompt/skill?

1. **References** — Add #file: paths pointing to the standards (lightweight, stays in sync)
2. **Copy content** — Paste full standards content inline (self-contained, won't auto-update)

Which approach? (1 or 2)
```

**If References:**
```
Include references to these standards files in the appropriate location:

#file:agent-os/standards/[folder]/[file].md
#file:agent-os/standards/[folder]/[file].md
```

**If Copy content:** Paste the full file contents inline.

---

#### Scenario: Planning/Spec

Same options as Prompt/Skill scenario, but framed as inclusion in a plan document.

---

### Step 6: Surface Related Prompts (Conversation scenario only)

After injecting, check if `.github/prompts/` contains related prompts and mention them:

```
Related prompts you might want to use:
- [prompt-name] — [brief description]
```

---

## Explicit Mode

When arguments are provided, skip the suggestion step but still detect scenario, then validate and inject the specified files/folders.

If a specified file/folder doesn't exist:
```
Standard not found: [path]

Available standards in [folder]/:
- [file1]
- [file2]

Did you mean one of these?
```

## Tips

- **Inject early** — Add standards at the start of a task, before implementation
- **Be specific** — Use explicit mode when you know which standards apply
- **Check the index** — If suggestions seem wrong, run the index-standards prompt to rebuild
- **Keep standards concise** — Injected standards consume context; shorter is better
