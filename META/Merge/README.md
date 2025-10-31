# 📦 Merge Playbook Hub

**Updated on:** 2025-02-15

## 🎯 Mission
Unify functionality from `repoA/` into the architectural style and conventions of `repoB/`, while honoring that every top-level folder in this monorepo is treated as an independent Git repository with its own workflows.

## 🗺️ Directory Scope
- `repoA/` → Source functionality to analyze, decompose, and map into the target design.
- `repoB/` → Destination framework whose patterns, interfaces, and conventions must be adopted.
- `META/Merge/` → Coordination hub for planning documents, merge scripts, status reports, and agent outputs.

## 🧠 Agents in This Area
Refer to [`AGENTS.md`](./AGENTS.md) for active roles:
- `MetaMergeCoordinator` orchestrates end-to-end planning and delegates to specialists.
- `RepoDiscoveryAgent` inventories both repositories as separate origins.
- `RefactorizationAgent` rebuilds or adapts repoA systems into repoB form.
- `VerificationAgent` enforces parity checks and regression coverage.
- `SafetyAgent` guards against leaking sensitive data during planning and execution.

## 🧾 Operating Principles
1. **Repository Isolation:** Never assume shared history. Use subtree, submodule, or archival exports when transferring code between folders.
2. **Traceable Migration Plans:** Document mappings from repoA modules to repoB destinations before coding. Update the plan with progress notes, blockers, and decisions.
3. **Incremental Refactorization:** Favor staged rollouts—introduce adapters or facades that let repoB coexist with legacy repoA components until parity is confirmed.
4. **Verification First:** Every migrated feature must include tests that run under repoB's toolchain. Keep repoA's original tests as reference until replaced.
5. **Safety Checks:** Run secret-scanning and policy validation on all merge artifacts prior to sharing or committing.

## 🛠️ Suggested Workflow
1. **Discover & Document** — Run the `RepoDiscoveryAgent` to capture structure, dependencies, and tooling for both repos.
2. **Plan the Merge** — Use `MetaMergeCoordinator` to create a feature-by-feature mapping and backlog.
3. **Refactor & Build** — Execute tasks via `RefactorizationAgent`, producing new files, subsystems, and documentation in repoB style.
4. **Verify & Iterate** — Engage `VerificationAgent` to run dual test suites and record outcomes.
5. **Finalize & Secure** — Let `SafetyAgent` audit artifacts before sign-off.

## 📚 Logbook Template
Record major decisions and progress in this README using the template below:

```markdown
### YYYY-MM-DD — Milestone Title
- **Summary:** What changed or was learned.
- **RepoA Impact:** Modules/features ready for migration or already migrated.
- **RepoB Impact:** New components created, tests added, or refactors completed.
- **Open Risks:** Outstanding issues, uncertainties, or follow-up work.
- **Next Steps:** Actionable items for the team.
```

## 📮 Contact & Ownership
- **Primary Owner:** MetaMergeCoordinator (automated)
- **Human Liaison:** Assign a maintainer per merge initiative and note them here.

> “Every repository is its own story—our job is to weave them into a coherent narrative.”
