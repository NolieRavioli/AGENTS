# Eve Data Framework Agent Suite

Updated on 2025-10-29

## Overview
The Eve Data Framework Agent Suite describes how autonomous collaborators coordinate on Eve-powered REST APIs that sit on top of MongoDB. Each agent specializes in a key area—resource schemas, business logic hooks, security, deployment, and documentation—while a MetaAgent orchestrates their efforts.

## Quickstart
1. **Review the Charter**: Read [`AGENTS.md`](AGENTS.md) to understand the MetaAgent workflow and each specialist’s mandates.
2. **Set Up Environment**:
   - Install Python ≥3.12 and MongoDB (local or containerized).
   - Create a virtual environment and install Eve with pinned dependencies: `pip install "eve==1.2.4" "cerberus==1.3.5"`.
   - Export `EVE_SETTINGS=python_eve_settings.py` or point to your configuration module.
3. **Bootstrap Project Structure**:
   - Create `domain/` modules for resource schemas and register them in `settings.py`.
   - Add `hooks/` packages for business rules; wire them in `app.py`.
   - Provide `.env.example` and deployment manifests under `deploy/`.
4. **Coordinate Agents**: When planning work, involve the MetaAgent first so it can assign EveResourceArchitect, HookCraftsmanAgent, EveSecuritySentinel, DeploymentNavigator, or EveNarratorAgent as needed.

## Agent Highlights
| Agent | Focus | Key Deliverables |
| --- | --- | --- |
| MetaAgent | Delegation & sequencing | Task plans, conflict resolution, audit of mandates |
| EveResourceArchitect | Domain schemas & datasource tuning | `domain/*.py`, `settings.py` updates, Cerberus rules |
| HookCraftsmanAgent | Eve hooks & custom endpoints | `hooks/*.py`, blueprint modules, resilience wrappers |
| EveSecuritySentinel | AuthN/Z & defensive config | RBAC policies, CORS/rate limits, secure settings |
| DeploymentNavigator | Packaging & CI/CD | Dockerfiles, compose stacks, pipeline manifests |
| EveNarratorAgent | Documentation & guides | README updates, HAL examples, onboarding docs |

## Best Practices
- Prefer declarative Eve schemas over imperative validation logic.
- Keep hook functions idempotent and guard external requests with retries/timeouts.
- Use structured logging and correlation IDs across services.
- Mirror production MongoDB indexes in development to surface performance issues early.
- Mock MongoDB using `mongomock` or containers during automated testing.

## Further Reading
- [Eve Official Documentation](https://docs.python-eve.org/)
- [Cerberus Validation Rules](https://docs.python-cerberus.org/)
- [MongoDB Indexing Strategies](https://www.mongodb.com/docs/manual/indexes/)

## Contribution Guidelines
1. Update both `AGENTS.md` and this README when introducing new agents or altering responsibilities.
2. Document new resources with example payloads and mention relevant authentication scopes.
3. Run linting (`ruff`, `mypy`) and security scans (`bandit`) before submitting changes.
4. Include changelog entries for API-breaking or security-impacting updates.

## Changelog
- **2025-10-29** — Initial Eve Data Framework agent suite published.
