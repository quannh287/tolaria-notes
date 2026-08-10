# Tolaria — Second Brain

Welcome to your personal knowledge base! This workspace is a **Tolaria vault**: a flat directory of portable Markdown files enriched with YAML frontmatter to form a rich, semantic personal knowledge graph. 

Tolaria is a markdown-based, git-first, offline-first personal knowledge base built by [Luca Rossi](https://refactoring.fm) to manage a 10,000+ note knowledge base with zero lock-in and complete data ownership.

---

## 🚀 Getting Started

To explore this vault and learn how Tolaria works, follow these steps:

1. **Launch Tolaria** or open this folder in your favorite Markdown editor (e.g., VS Code, Obsidian, or Tolaria Desktop).
2. Open the main interactive walkthrough note:  
   👉 **[`Getting Started/get-familiar-with-tolaria.md`](Getting%20Started/get-familiar-with-tolaria.md)**
3. Use `Cmd+Click` (or your editor's "follow link" shortcut) on any `[[wikilinks]]` to navigate across notes, topics, and walkthroughs.

---

## 💡 Core Philosophy

Tolaria is built on a few core principles that guide its design and features:

*   📑 **Files-first:** Your notes are plain Markdown files. They are portable, work with any editor, and require no proprietary export step.
*   🔌 **Git-first:** Every vault is a git repository. You get full version history, conflict resolution, sync status, and zero dependency on proprietary cloud servers.
*   🛜 **Offline-first & zero lock-in:** No mandatory accounts, no subscriptions, and works completely offline. If you stop using Tolaria, you lose nothing.
*   📋 **Standards-based:** Notes use standard YAML frontmatter for properties and relationships.
*   🔍 **Types as lenses:** Note types are navigation aids, not schema enforcement mechanisms. There are no mandatory fields—just useful categories.
*   🪄 **AI-first:** Designed to interact seamlessly with AI agents while keeping you in full control.

---

## 🗂️ Vault Anatomy

Here is how a Tolaria vault is organized structurally:

```text
second-brain/
├── Getting Started/                 # Main Tolaria vault directory (Git-tracked)
│   ├── attachments/                 # Image assets, screenshots, and PDFs
│   ├── views/                       # Saved custom list/kanban view configurations
│   │   └── active-projects.yml
│   ├── AGENTS.md                    # Guidelines for AI agents on formatting & conventions
│   ├── GEMINI.md                    # Compatibility shim for Gemini CLI
│   ├── CLAUDE.md                    # Compatibility shim for Claude Code
│   ├── get-familiar-with-tolaria.md # Interactive walkthrough start note
│   ├── tolaria-principles.md        # Core philosophy and values
│   ├── ...                          # flat .md notes (notes, people, projects, topics)
│   └── type.md / project.md / ...   # Note-type definitions (Person, Project, Topic, etc.)
└── README.md                        # This file (Workspace-level introduction)
```

### Note Conventions

*   **Flat files:** Most notes live flat at the vault root.
*   **H1 Headers:** The first `# Header` in the body is the preferred display title of the note.
*   **YAML Frontmatter:** Used to manage metadata, status, and custom properties:
    ```yaml
    ---
    type: Project
    status: Active
    icon: target
    Related to: "[[tolaria]]"
    ---
    # Ship Tolaria
    ```
*   **Wikilinks:** Links like `[[note-filename]]` or `[[note-filename|Display Text]]` are fully supported in both the frontmatter relationships and the Markdown body.

---

## 🤖 AI & MCP Integration

Because Tolaria is built on plain text files with clear, structured markdown conventions, it is extremely easy to use with local and remote AI assistants.

### Claude Desktop Integration (MCP)

Tolaria includes an official **Model Context Protocol (MCP)** server, allowing AI assistants like Claude Desktop to search, read, write, and interact directly with your vault files.

The MCP server has been configured in your **Claude Desktop** global config at `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "tolaria": {
      "command": "/Users/quannh2871/.bun/bin/bun",
      "args": [
        "/Applications/Tolaria.app/Contents/Resources/mcp-server/index.js"
      ],
      "env": {
        "WS_UI_PORT": "9711"
      },
      "type": "stdio"
    }
  }
}
```

This lets Claude Desktop understand your entire personal knowledge graph, follow wikilinks, and update your second brain with perfect formatting.

### Guidelines for AI Agents (`AGENTS.md`)

If you are using external command-line agents (like `claude` or `gemini`), they can refer to **[`Getting Started/AGENTS.md`](Getting%20Started/AGENTS.md)** to understand the exact formatting rules, directory structures, and note-writing conventions of this vault.

---

## 🛠️ Explore the Walkthroughs

Dive into specific features inside the vault by checking out these documents:

*   **[Tolaria Sidebar](Getting%20Started/tolaria-sidebar.md):** How the Inbox, All Notes, Archive, Favorites, and Folders work.
*   **[Tolaria Note List](Getting%20Started/tolaria-note-list.md):** Learn sorting, display properties, and filtering.
*   **[Tolaria Editor](Getting%20Started/tolaria-editor.md):** Markdown editor, WYSIWYG mode, and wikilink autocompletion.
*   **[Properties Panel](Getting%20Started/the-properties-panel.md):** Manage types, metadata fields, and relationships easily.
*   **[AI in Tolaria](Getting%20Started/tolaria-ai.md):** Quick prompt mode (`Cmd+K` + Space) and the persistent AI Panel.
*   **[Multiple Vaults](Getting%20Started/multiple-vaults.md):** Working with multiple folders or repositories in a unified graph.
*   **[Auto Git](Getting%20Started/autogit.md):** Automatic background backups and sync status.
