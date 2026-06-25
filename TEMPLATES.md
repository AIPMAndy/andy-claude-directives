# CLAUDE.md Templates

Pre-configured templates for different use cases. Pick one as a starting point and customize.

---

## Template 1: Minimal (Core Principles Only)

For teams that want just the essential behavioral guidelines without the cognitive framework.

```markdown
# CLAUDE.md

## Core Principles

### 1. Think Before Coding
- State assumptions explicitly
- Present options when multiple interpretations exist
- Ask when unclear

### 2. Simplicity First
- Write minimum code that solves the problem
- No abstractions for single-use code
- No features beyond what was asked

### 3. Surgical Changes
- Only modify what's necessary
- Match existing code style
- Don't refactor unrelated code

### 4. Goal-Driven Execution
Transform tasks into verifiable goals:
- "Add validation" → Write tests for invalid inputs, then make them pass
- "Fix bug" → Write a reproducing test, then make it pass

For multi-step tasks:
1. [Step] → Verify: [check]
2. [Step] → Verify: [check]

## Tech Stack
- Language: [Your language]
- Framework: [Your framework]
- Package Manager: [Your package manager]
- Database: [Your database]

## Project Rules
- [Add project-specific rules here]
```

---

## Template 2: Full Stack (Complete Directives)

The complete version from this repo - best for complex projects.

Simply copy [`CLAUDE.md`](./CLAUDE.md) from this repo.

---

## Template 3: Data-Centric (Focus on Data Integrity)

For analytics, reporting, or data processing projects where accuracy is critical.

```markdown
# CLAUDE.md

## Data Integrity Principles (CRITICAL)

**Absolutely prohibit fabrication, guessing, or beautification of any data.**

### Rules
1. **Only report verified data**
   - Image unclear → Say "cannot identify", don't guess
   - Tool returns data → Quote verbatim, don't polish
   - Show calculation process for all computations

2. **Standard phrases for uncertainty**
   - ❌ "About XX" "Estimate XX" "Should be XX"
   - ✅ "Data shows XX, but the following fields cannot be confirmed: [list]"
   - ✅ "I cannot read this data, need your confirmation"

3. **Data presentation checklist**
   - [ ] Where does this data come from? (Source/tool/calculation)
   - [ ] Did I verify every digit?
   - [ ] Can I point to the original source if questioned?

4. **Prohibited behaviors**
   - Guessing numbers from blurry images
   - Beautifying data to make reports "look good"
   - Using "approximately" to mask uncertainty

### Error Handling
- Admit immediately when wrong
- Point out error source
- Re-verify and provide accurate data
- No excuses

## Core Coding Principles
[Include sections 1-4 from Template 1]

## Tech Stack
[Your stack details]
```

---

## Template 4: Startup/MVP (Speed + Safety Balance)

For fast-moving teams that need speed but want to avoid common pitfalls.

```markdown
# CLAUDE.md

## Development Philosophy
**Move fast, but don't break things unnecessarily.**

### Speed Guidelines
✅ **Do quickly:**
- MVP features with explicit scope
- Simple CRUD operations
- Standard patterns from our stack
- Obvious bug fixes

❌ **Ask first:**
- Database schema changes
- Breaking API changes
- New dependencies
- Auth/security changes

### Coding Principles

**1. Ask when unclear**
If requirements could mean multiple things, list 2-3 interpretations and ask.

**2. Implement the simplest thing**
No abstractions until we have 3+ use cases. Copy-paste is fine for MVPs.

**3. Keep changes focused**
When fixing A, don't also refactor B "while you're there."

**4. Test before claiming done**
Run the app/tests to verify. If something broke, fix it before responding.

### Multi-Step Plan Format
For non-trivial features, state brief plan:
```
1. [Step] → Verify: [how you'll check it works]
2. [Step] → Verify: [how you'll check it works]
```

### Tech Stack (Locked)
- Language: [Your language]
- Framework: [Your framework]
- Database: [Your database]
- **Don't suggest alternatives** unless explicitly broken

### Safety Stops
These require explicit "yes" confirmation:
- Dropping database tables
- Deleting multiple files
- Force pushing to git
- Modifying .env files
```

---

## Template 5: Solo Developer (Conversational + Pragmatic)

For individual developers who want guidance without formality.

```markdown
# CLAUDE.md

## How I Work

**Communication**
- I prefer concise responses over verbose explanations
- If something's unclear, I'll ask before coding
- For big changes, I'll outline the plan first

**My coding style**
- Simple over clever
- Only change what needs changing
- Match the existing code style
- Test before saying "done"

**Before you implement anything non-trivial, tell me:**
1. What you're going to change
2. Why this approach
3. What you'll verify to confirm it works

If there are multiple ways to do it, show me options.

**Tech stack I'm using:**
- [Your stack here]

**Things to never do without asking:**
- Change the database schema
- Add new dependencies
- Delete files
- Modify production configs

**When you're uncertain:**
Just say "I'm not sure about X, here's what I think..." and I'll clarify.

## Memory
Track key decisions in `DECISIONS.md`:
- What was decided
- Why
- What alternatives were rejected

Check that file before suggesting solutions to recurring problems.
```

---

## Template 6: Team/Enterprise (Strict Governance)

For teams with strict review processes and compliance needs.

```markdown
# CLAUDE.md

## Development Standards

### Pre-Implementation Checklist
Before writing code for any feature:
- [ ] Requirements are unambiguous
- [ ] Acceptance criteria are defined
- [ ] Technical approach is documented
- [ ] Security implications assessed
- [ ] Breaking changes identified

### Code Change Principles

**1. Think Before Coding**
- State all assumptions explicitly
- Present multiple approaches when applicable
- Identify risks and tradeoffs

**2. Minimize Blast Radius**
- Only modify files directly related to the task
- No "drive-by" refactoring
- No style/formatting changes unless that's the task
- Each commit = one logical change

**3. Verify Everything**
- All changes must have automated tests
- Run full test suite before claiming complete
- Document what was manually tested
- Note what could NOT be verified

**4. Document Decisions**
For non-trivial implementations, document:
- Why this approach was chosen
- What alternatives were considered
- What tradeoffs were made

### Safety Requirements

**Require explicit approval before:**
- Modifying database schema
- Changing authentication/authorization
- Adding dependencies
- Modifying CI/CD configs
- Deploying to production
- Deleting data or files
- Force pushing to git

**Security**
- Never log sensitive data
- Never commit secrets
- Always validate user input
- Follow principle of least privilege

### Tech Stack
[Your stack with version requirements]

### Compliance
- All code changes must be traceable to a ticket/issue
- All database changes must have migration scripts
- All API changes must update OpenAPI spec
- Security changes require security team review
```

---

## How to Choose

| Your Situation | Recommended Template |
|----------------|---------------------|
| Just want to reduce LLM mistakes | **Template 1: Minimal** |
| Complex project with many dependencies | **Template 2: Full Stack** |
| Data science, analytics, reporting | **Template 3: Data-Centric** |
| Early-stage startup building MVP | **Template 4: Startup/MVP** |
| Solo developer, side project | **Template 5: Solo Developer** |
| Enterprise, compliance requirements | **Template 6: Team/Enterprise** |

---

## Customization Tips

After picking a template:

1. **Add your tech stack details**
   - Lock dependencies you don't want changed
   - Specify preferred tools/libraries

2. **Add project-specific rules**
   - Naming conventions
   - File organization
   - Git workflow

3. **Add domain knowledge**
   - Business rules
   - Edge cases to always handle
   - Common gotchas

4. **Add memory pointers**
   - Where decisions are documented
   - Where to find examples
   - Key files to read before changes

5. **Test it**
   - Give Claude a task
   - See if it asks the right questions
   - Adjust guidelines based on what's missing

---

## Combining Templates

You can mix sections from multiple templates:

```markdown
# CLAUDE.md

## Core Principles
[From Template 1]

## Data Integrity
[From Template 3]

## Safety Requirements
[From Template 6]

## Tech Stack
[Your details]
```

Start simple, add complexity only when needed.
