---
title: "Open Questions — Resolved"
owners: [liuchao001]
status: approved
---

# Open Questions — Resolved

Questions raised during doc planning. All resolved by team discussion on 2026-03-19.

---

## Q1: Multiple owner conflict

**Question:** If a node has multiple owners and they disagree (one approves, one rejects), what happens?

**Decision:** All owners must approve (AND logic). Every owner must approve to move to the next step. If any owner rejects, the change is blocked.

---

## Q2: Tree maintenance process

**Question:** When code and tree are out of sync, how does it stay current?

**Decision:** The Context Tree is the _decision layer_. The codebase is the _execution layer_. These two layers are separated and independent.

- The decision layer does not have execution layer context. The tree does not look at code.
- The execution layer does not change the decision layer. Code does not modify the tree.
- Agents must follow NODE.md when implementing. The tree is the source of truth.
- **Reviewer agent:** checks that PRs in the codebase have no conflict with NODE.md.
- **Maintainer agent:** periodically checks code/doc alignment (cron job). If execution diverges from the decision, the maintainer flags it, but the tree is not auto-updated from code.

```
Decision Layer (Tree)          Execution Layer (Code)

  decisions ──────────▶ guide ──────────▶ implementation
  designs                                  code
  ownership                                configs

  Tree tells code WHAT to do.
  Code does NOT tell tree what it decided.
  They live in separate repos.
  They are independent.
```

---

## Q3: Librarian agent pattern

**Question:** Should there be a dedicated agent for code/doc alignment?

**Decision:** Covered by Q2. Two agent roles replace the single Librarian concept:

1. **Reviewer agent** — checks PRs against NODE.md for conflicts
2. **Maintainer agent** — cron job that periodically checks alignment

---

## Q4: Fallback for mistakes

**Question:** What if someone approves or rejects by mistake?

**Decision:** Create a new PR. Fallback is always through a new PR, maintaining clean git history. No out-of-band reverts.

---

## Q5: Stale/deprecated nodes

**Question:** How do agents identify stale or deprecated nodes?

**Decision:** Node owner must maintain and state in a new NODE.md that the previous one is deprecated. Deprecation is owner-driven. Agents do not auto-deprecate.

---

## Q6: Default tree templates

**Question:** Should there be starter templates to prevent flat file dumps?

**Decision:** Tree structure is always sorted based on agent-optimized domain knowledge search. When a new NODE.md is proposed, the tree autonomously restructures itself for optimal agent navigation.

---

## Q7: TUI for init onboarding

**Question:** Should there be a TUI to help teams set up?

**Decision:** Accepted as a feature proposal. To be built as part of the CLI.

---

## Key Architectural Decision: Decision Layer vs Execution Layer

The Context Tree is the **decision layer**. Codebases are the **execution layer**. They are separated.

- The decision layer contains: why, what, who, when, design decisions, ownership, principles.
- The execution layer contains: how, code, configs, implementations.
- The tree does NOT have codebase context. It does not read code.
- Code does NOT change the tree. Implementation does not modify decisions.
- Agents in the execution layer must follow the tree. The tree is the source of truth.
- If execution diverges from decision, a reviewer or maintainer agent flags it. But the tree is not auto-updated from code.

This separation keeps the tree clean, stable, and authoritative. The tree is law. Code follows.
