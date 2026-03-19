---
title: "Open Questions"
owners: [liuchao001]
status: draft
---

# Open Questions

Questions raised during doc planning that need team discussion and decisions.

---

## Q1: Multiple owner conflict

If a node has multiple owners and they disagree (one approves, one rejects), what happens?

**Proposed answer:** Any owner can approve (OR logic). Rejection blocks with a required explanation. NODE.md owner is the final tiebreaker since Rule 1 says NODE.md is the folder-level authority. If two NODE.md co-owners keep disagreeing, split the domain into two subtrees with clear single owners.

**Status:** needs team decision

---

## Q2: Tree maintenance process

When code changes and the doc is now out of sync (e.g. product spec says features A, B, C but engineers dropped C during implementation), how does the tree stay current?

Three models:

- **Human updates:** Engineer opens a PR on the tree after changing code. Relies on humans remembering.
- **Agent detects drift:** An autonomous agent periodically compares code to tree nodes and opens PRs when they diverge. Node owner reviews.
- **CI/CD triggers:** On every merge to main, a workflow checks if the change relates to any tree node and notifies the owner or triggers an agent to draft an update.

**Proposed answer:** All three are valid. Agent drift detection is the native model. The agent is the Librarian. It maintains what humans forget. But humans still approve.

**Status:** needs team decision

---

## Q3: Can agents approve or reject PRs?

Can approval/rejection only be done by humans manually, or can agents do it too?

**Proposed answer:** Yes, agents can approve and reject. If an agent is listed as an owner of a node, it has the same authority as a human owner. That is the whole point of "agents as peers." An owner is an owner regardless of whether they are human or agent.

A human owner's personal agent (their clone/assistant) could also act on their behalf if the human has delegated that permission. This ties into the Identity pillar: permission delegation is explicit and revocable.

**Status:** needs team decision

---

## Q4: What if someone (human or agent) approves or rejects by mistake?

Fallback mechanisms for incorrect actions.

**Proposed answer:** Git is the fallback. Every action is a commit.

- **Mistaken approval (merged something wrong):** Revert the commit. Git revert creates a new commit that undoes the change. The history shows what happened and why it was reverted. The tree is never truly broken because you can always roll back.
- **Mistaken rejection:** Reopen the PR. The rejection reason is in the PR history. The author or another owner can override.
- **Agent acting incorrectly:** The agent's owner (the human who delegated permissions) can revoke the delegation. The Identity pillar specifies that permissions are "explicit and revocable."

Three layers of safety:

1. **Git history.** Every action is recorded. Nothing is permanently lost. Revert any commit.
2. **NODE.md hierarchy.** A parent NODE.md owner can always override a child. The root owner is the final backstop.
3. **Permission revocation.** If an agent is making bad decisions, its permissions can be revoked by the human who granted them.

**Status:** needs team decision

---

## Q5: Is there a dedicated agent for code/doc alignment?

Should there be a specific agent role that watches code changes and keeps tree nodes in sync, running periodically?

**Proposed answer:** Yes. This is the "Librarian agent" pattern. An agent that:

- Runs continuously or on a schedule
- Owns or watches the documentation subtrees
- Monitors code changes (via git hooks, CI triggers, or periodic scans)
- Opens PRs on tree nodes when it detects drift
- Node owners (human or agent) review and approve

This is not defined in the current standard as a requirement, but it is a recommended pattern. The standard defines the tree format and ownership rules. How teams maintain the tree (manually, with agents, or with CI) is up to them. But the Librarian agent is the intended model.

**Status:** needs team decision
