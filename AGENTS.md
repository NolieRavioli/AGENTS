# AGENTS.md
# 🤖 Codex Agent Architecture
**Repository:** https://github.com/NolieRavioli/AGENTS  
**Purpose:** To define, generate, and maintain structured `AGENTS.md` and `README.md` hierarchies for language- or framework-specific subprojects.

---

## 🧩 Meta Design

Each folder within this repository represents a **language** or **framework specialization**.  
Each specialization may have one or more *sub-agents* (e.g., “Basic”, “Flask-Based”, “Embedded”, etc.) that maintain their own `AGENTS.md` and `README.md`.

Example layout:
```
AGENTS/
├─ README.md
├─ Python/
│ ├─ Basic/
│ │ ├─ AGENTS.md
│ │ └─ README.md
│ └─ Flask-Based/
│ ├─ AGENTS.md
│ └─ README.md
└─ C++/
└─ Basic/
├─ AGENTS.md
└─ README.md
```

---

## 🧠 MetaAgent
**Purpose:**  
Coordinate all sub-agents, interpret the current `AGENTS.md`, and decide which agent(s) to invoke based on repository context.

**Responsibilities:**  
- Discover `AGENTS.md` files recursively.  
- Parse context (language, framework, directory name).  
- Delegate task generation to the most relevant sub-agent.  
- Enforce *secrecy constraints* (no credentials, tokens, URLs, or filesystem paths).  
- Produce or update new `AGENTS.md`/`README.md` skeletons when missing.

**Rules:**  
- Never output or commit sensitive data.  
- Always include structured metadata headers.  
- Summarize which sub-agents acted and why.

**Example workflow:**
1. MetaAgent scans `repo/`.
2. Detects `Python/Flask-Based/`.
3. Loads `FlaskAgent` and `HTMLAgent`.
4. Instructs them to build framework-specific templates.
5. Generates `README.md` summarizing agent hierarchy.

---

## 🏗️ BuilderAgent
**Purpose:**  
Generate standardized agent folders and Markdown templates for new projects.

**Responsibilities:**  
- Create `/Language/Variant/AGENTS.md` and `/README.md`.  
- Apply naming conventions and metadata blocks.  
- Validate structural consistency (headers, emojis, schema).

**Rules:**  
- Always generate UTF-8 Markdown with Unix newlines.  
- Automatically include a MetaAgent section.  
- Never duplicate existing agent definitions verbatim.  
- Must pass Markdown lint checks.

**Triggers:**  
“create new agent folder”, “bootstrap AGENTS.md”, “initialize README.md”.

---

## 🧾 DocsAgent
**Purpose:**  
Generate detailed and readable documentation for each agent or subproject.

**Responsibilities:**  
- Build `README.md` for each subdirectory.  
- Include summaries of all agents, roles, and examples.  
- Maintain cross-links between related agents (e.g., Python ↔ Flask-Based).  
- Embed auto-generated TOC and metadata header.

**Rules:**  
- Always explain *how* and *why* an agent operates.  
- Use Markdown headings (`##`, `###`) and emoji tags.  
- Include “Updated on {date}” footer.

---

## 🧩 Language MetaAgents

### 🐍 PythonMetaAgent
**Purpose:**  
Oversee all Python-related agents and their behavior.

**Sub-agents:**
- `Python/Basic/AGENTS.md` → defines CodeAgent, DocsAgent, TestAgent  
- `Python/Flask-Based/AGENTS.md` → defines FlaskAgent, HTMLAgent, WebAppAgent, SecurityAgent  

**Rules:**  
- PythonMetaAgent detects Flask, FastAPI, or CLI frameworks automatically.  
- Avoid environment-specific info like hostnames or secrets.  
- Apply PEP8 + type hints to all generated examples.

---

### 💻 CppMetaAgent
**Purpose:**  
Manage all C++ agents (Basic, Embedded, Cross-Platform).

**Sub-agents:**
- `C++/Basic/AGENTS.md` → CodeAgent, BuildAgent, TestAgent  
- `C++/Embedded/AGENTS.md` (optional) → HardwareAgent, MemoryAgent

**Rules:**  
- Generate portable examples (C++17+).  
- Use descriptive comments, not inline debugging output.  
- Never embed local include paths.

---

### 🌐 WebMetaAgent
**Purpose:**  
Coordinate all agents related to front-end or web environments.

**Sub-agents:**
- `HTMLAgent` → generates HTML/JS templates
- `CSSAgent` → defines style consistency rules
- `APIAgent` → describes REST/GraphQL endpoints
- `SecurityAgent` → ensures proper sanitization and auth patterns

**Rules:**  
- Must not output user data, API tokens, or domains.  
- Focus on reproducible templates, not live credentials.  
- Enforce HTTPS and content-security-policy best practices.

---

## 🔒 SafetyAgent
**Purpose:**  
Guarantee that no sensitive or environment-specific information leaks into generated documents.

**Responsibilities:**  
- Scrub secrets from text before commit.  
- Detect domain names, file paths, email addresses, and tokens via regex.  
- Replace with generic placeholders (`example.com`, `/path/to/dir`, `user@host`).

**Rules:**  
- Always run before MetaAgent commit actions.  
- Log which items were redacted and why.  
- Non-interactive, always enforce “safe-by-default”.

---

## 🧰 UtilityAgent
**Purpose:**  
Provide shared functions for all agents (date stamping, Markdown validation, path sanitization).

**Responsibilities:**  
- Validate headings and Markdown schemas.  
- Insert timestamps and metadata tags.  
- Manage relative links between nested `AGENTS.md`.

---

## 🧭 Global Architecture Rules
1. **Structure:** Every subdirectory must contain both `AGENTS.md` and `README.md`.  
2. **Consistency:** All agents must declare Purpose, Style, Scope, Rules, Tools, and Triggers.  
3. **Delegation:** Each `AGENTS.md` must contain at least one MetaAgent coordinating the others.  
4. **Safety:** No secret information is ever included — only public templates or placeholders.  
5. **Reproducibility:** Any agent definition must be reproducible on a clean environment with no credentials.

---

## 📚 Example Generation Flow

```
MetaAgent invoked on /Python/Flask-Based
→ Loads PythonMetaAgent → Delegates to FlaskAgent
→ FlaskAgent builds new Flask/Blueprint agent folder
→ DocsAgent writes README.md describing endpoints
→ SafetyAgent cleans for secrets
→ MetaAgent commits result
```

---

## 🧩 Output Schema for Generated `AGENTS.md`
Each generated file must follow this minimal schema:

```markdown
# AGENTS.md
## MetaAgent
- Purpose: Coordinates sub-agents and context
- Rules: Summarize, delegate, sanitize

## <PrimaryAgentName>
- Purpose: ...
- Style: ...
- Scope: ...
- Rules: ...
- Tools: ...
- Triggers: ...
```

## 🕹️ Example MetaAgent Invocation

```bash
python metaagent.py --init Python/Flask-Based
```
Expected result:
```
Python/Flask-Based/
├─ AGENTS.md      # contains FlaskAgent, HTMLAgent, SecurityAgent
└─ README.md      # auto-generated summary
```

---

> “Agents don’t just build code; they build the framework that builds the next generation of agents.”  
> — AGENTS.md Prime Directive

