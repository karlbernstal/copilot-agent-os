# Agent OS for Github Copilot

## Agents that build the way you would

[Agent OS](https://buildermethods.com/agent-os) helps you shape better specs, keeps agents aligned in a lightweight system that fits how you already build.

Works with **GitHub Copilot** and any AI tool that supports `.prompt.md` files. Any language, any framework.

**Core capabilities:**

- **Discover Standards** — Extract patterns and conventions from your codebase into documented standards
- **Deploy Standards** — Intelligently inject relevant standards based on what you're building
- **Shape Spec** — Create better plans that lead to better builds
- **Index Standards** — Keep your standards organized and discoverable

---

### How it works

Agent OS prompts live in `prompts/agent-os/` in this repo. When you run the install script, they are copied into your project's `.github/prompts/` folder, making them available as GitHub Copilot prompts (or any compatible tool).

Each prompt file uses the `.prompt.md` format with an `agent: agent` frontmatter attribute, targeting the built-in **agent** mode for autonomous, multi-step tasks.

#### Prompts included

| Prompt | Description |
|---|---|
| `discover-standards` | Extract tribal knowledge from your codebase into documented standards |
| `index-standards` | Rebuild and maintain `agent-os/standards/index.yml` |
| `inject-standards` | Inject relevant standards into the current context |
| `plan-product` | Establish foundational product docs (mission, roadmap, tech stack) |
| `shape-spec` | Gather context and structure a spec/plan for significant work |

---

### Compatibility

This fork targets tools that use the **`.prompt.md`** convention:

- ✅ GitHub Copilot (agent mode)
- ✅ Any tool supporting `.github/prompts/` prompt files

> **Note:** This version does **not** include Claude Code slash-commands (`/command` style). For the original Claude Code version, see the [upstream Agent OS repo](https://buildermethods.com/agent-os).

---

### Installation

Run the install script from your project directory, pointing it at wherever you cloned this repo:

```bash
bash /path/to/copilot-agent-os/scripts/project-install.sh
```

This will:
1. Create `agent-os/` project structure
2. Copy standards from your chosen profile into `agent-os/standards/`
3. Build `agent-os/standards/index.yml`
4. Copy all prompts into `.github/prompts/`

To update only the prompts without touching your standards:

```bash
bash /path/to/copilot-agent-os/scripts/project-install.sh --commands-only
```

---

### Repo structure

```
prompts/agent-os/       # Source prompt files (.prompt.md)
profiles/               # Standards profiles (default, and custom)
scripts/                # Install and sync scripts
config.yml              # Default profile and version config
```

---

### Documentation & Installation

Docs, usage, & best practices 👉 [It's all here](https://buildermethods.com/agent-os)

---

### Follow updates & releases

Read the [changelog](CHANGELOG.md)

[Subscribe to be notified of major new releases of Agent OS](https://buildermethods.com/agent-os)

---

### Created by Brian Casel @ Builder Methods

Created by Brian Casel, the creator of [Builder Methods](https://buildermethods.com), where Brian helps professional software developers and teams build with AI.

Get Brian's free resources on building with AI:
- [Builder Briefing newsletter](https://buildermethods.com)
- [YouTube](https://youtube.com/@briancasel)

Join [Builder Methods Pro](https://buildermethods.com/pro) for official support and connect with our community of AI-first builders:
