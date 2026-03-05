---
agent: agent
description: Rebuild and maintain the agent-os/standards/index.yml file
---

# Index Standards

Rebuild and maintain the standards index file (`agent-os/standards/index.yml`).

## Purpose

The index enables the inject-standards prompt to suggest relevant standards without reading all files. It maps each standard to a brief description for quick matching.

## Process

### Step 1: Scan for Standards Files

List all `.md` files in `agent-os/standards/` and its subfolders. Build a list organized by folder:

```
root/coding-style.md        # Files directly in standards/ root use "root" as folder name
root/naming.md
api/response-format.md
database/migrations.md
```

**Note:** `root` is a reserved keyword for `.md` files directly in `agent-os/standards/` (not in a subfolder). Do not create an actual folder named "root".

### Step 2: Load Existing Index

Read `agent-os/standards/index.yml` if it exists. Note which entries already have descriptions.

### Step 3: Identify Changes

Compare the file scan with the existing index:
- **New files** — Standards files without index entries
- **Deleted files** — Index entries for files that no longer exist
- **Existing files** — Already indexed, keep as-is

### Step 4: Handle New Files

For each new standard file that needs an index entry:

1. Read the file to understand its content
2. Propose a description:

```
New standard needs indexing:
  File: [folder]/[filename].md

Suggested description: "[one-sentence description]"

Accept? (yes / or type a better description)
```

Keep descriptions to **one short sentence** — they're for matching, not documentation.

### Step 5: Handle Deleted Files

If there are index entries for files that no longer exist, remove them automatically (no confirmation needed) and report:

```
Removed [N] stale index entries: [file1], [file2]
```

### Step 6: Write Updated Index

Generate `agent-os/standards/index.yml` with this structure:

```yaml
folder-name:
  file-name:
    description: Brief description here
```

**Rules:**
- Alphabetize folders (`root` section first)
- Alphabetize files within each folder
- File names without `.md` extension
- One-line descriptions only

**Example:**
```yaml
root:
  coding-style:
    description: General coding style, formatting, linting rules
  naming:
    description: File naming, variable naming, class naming conventions

api:
  error-handling:
    description: Error codes, exception handling, error response format
  response-format:
    description: API response envelope structure, status codes, pagination

database:
  migrations:
    description: Migration file structure, naming conventions, rollback patterns
```
