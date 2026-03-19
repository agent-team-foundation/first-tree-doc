---
title: "What is Context Tree?"
owners: [liuchao001]
---

# What is Context Tree?

Context Tree is an open standard for organizational memory. It defines how teams of humans and AI agents structure, own, and navigate shared knowledge.

A Context Tree is a Git repository organized as a tree, where every node is a markdown file and every node has an owner. Agents read the tree to build context before acting. Humans read the tree to understand the current state of any domain. Both contribute to the tree as it grows.

The standard is open source, agent-agnostic, and designed for small, agent-centric teams.

---

## Index

### [01 Why It Exists](01-why-it-exists/NODE.md)

- [01.01 The Problem](01-why-it-exists/01.01-the-problem.md) — Why teams struggle with AI agents today, and the pattern we call _context routing_.
- [01.02 Agent Teams](01-why-it-exists/01.02-agent-teams.md) — What an Agent Team is: humans and AI agents working together as peers.
- [01.03 Design Principles](01-why-it-exists/01.03-design-principles.md) — Transparency, agents as first-class, tree over graph, git as foundation.

### [02 How It Works](02-how-it-works/NODE.md)

- [02.01 The Tree](02-how-it-works/02.01-the-tree.md) — A Context Tree is a Git repository organized as a hierarchy of markdown files.
- [02.02 Nodes](02-how-it-works/02.02-nodes.md) — NODE.md and leaf nodes: what they are and how they work.
- [02.03 Ownership](02-how-it-works/02.03-ownership.md) — The six ownership rules that govern who can change what.
- [02.04 Members](02-how-it-works/02.04-members.md) — How humans and agents are represented in the tree.
- [02.05 Soft Links](02-how-it-works/02.05-soft-links.md) — Cross-references between nodes without breaking the tree structure.
- [02.06 Frontmatter Reference](02-how-it-works/02.06-frontmatter-reference.md) — Every frontmatter field, formally defined.

### [03 Getting Started](03-getting-started/NODE.md)

- [03.01 Quick Start](03-getting-started/03.01-quick-start.md) — Initialize your first Context Tree in five minutes.
- [03.02 Writing Nodes](03-getting-started/03.02-writing-nodes.md) — How to write useful NODE.md and leaf node files.
- [03.03 Adding Members](03-getting-started/03.03-adding-members.md) — Represent your team in the tree.
- [03.04 Growing Your Tree](03-getting-started/03.04-growing-your-tree.md) — When to split, merge, and restructure.

### [04 Infrastructure](04-infrastructure/NODE.md)

- [04.01 Autonomous Agents](04-infrastructure/04.01-autonomous-agents.md) — Agents that run continuously and own domains.
- [04.02 Context Tree](04-infrastructure/04.02-context-tree.md) — The tree as infrastructure, in detail.
- [04.03 Message System](04-infrastructure/04.03-message-system.md) — How agents and humans communicate across domains.
- [04.04 Identity](04-infrastructure/04.04-identity.md) — Agent identity, permissions, and delegation.
- [04.05 Database](04-infrastructure/04.05-database.md) — Structured data, data lake, and data warehouse.
- [04.06 Workflow](04-infrastructure/04.06-workflow.md) — Deterministic automation alongside agent reasoning.

### [05 Developers](05-developers/NODE.md)

- [05.01 CLI](05-developers/05.01-cli.md) — Command-line interface reference.
- [05.02 API](05-developers/05.02-api.md) — API reference.

### [06 Examples](06-examples/NODE.md)

- [06.01 first-tree](06-examples/06.01-first-tree.md) — Walkthrough of the reference implementation.

### [07 Community](07-community/NODE.md)

- [07.01 Contributing](07-community/07.01-contributing.md) — How to contribute to Context Tree.
- [07.02 Links](07-community/07.02-links.md) — Discord, Twitter, blog, GitHub.

---

Context Tree is open source, built by [kael.im](https://kael.im).
