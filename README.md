# Andy's Core Operating Directives for Claude Code

A comprehensive behavioral guideline for Claude Code that combines fundamental cognitive axioms, Musk's engineering methodology, and Karpathy's coding principles to maximize execution quality and minimize common LLM mistakes.

## What This Is

This is a **CLAUDE.md** configuration file designed to make Claude Code:
- Think from first principles instead of surface analogies
- Question requirements before implementing
- Write minimal, surgical code changes
- Verify results systematically
- Handle uncertainty transparently

It's built on three pillars:
1. **9 Cognitive Axioms** (entropy law, reductionism, probabilistic uncertainty, etc.)
2. **Musk's 5-Step Engineering Method** (question → delete → simplify → accelerate → automate)
3. **Karpathy's 4 Coding Principles** (think before coding, simplicity first, surgical changes, goal-driven execution)

## Who This Is For

**Use this if you:**
- Want Claude to think more systematically and make fewer mistakes
- Need transparent reasoning and explicit uncertainty handling
- Value minimal, surgical code changes over "improvements"
- Want goal-driven execution with verifiable checkpoints
- Work on projects where data integrity is critical

**This is NOT:**
- A project template (no scaffolding, no CI/CD, no tech stack)
- An application framework
- A replacement for domain-specific instructions

## How to Use

### Option 1: Direct Use
Copy [`CLAUDE.md`](./CLAUDE.md) to your project root. Claude Code will automatically load it.

### Option 2: Merge with Existing CLAUDE.md
If you already have a `CLAUDE.md`, add the relevant sections:
- Copy the "Core Operating Directives" section to the top as high-level guidance
- Merge "Cognitive Axioms" if you want systematic reasoning
- Merge "Musk's 5-Step Method" if your project needs simplification discipline
- Merge "Karpathy's Principles" for better code quality

### Option 3: Customize
The file is modular. Keep what fits your workflow:
- **Cognitive Axioms**: For complex decision-making and system design
- **5-Step Method**: For avoiding over-engineering
- **Karpathy's Principles**: For code quality and maintainability
- **Data Integrity**: For projects with strict accuracy requirements
- **Safety Guardrails**: For production systems

## What Makes This Different

Most CLAUDE.md files focus on "how to code." This one focuses on **"how to think"** before coding:

1. **Cognitive Foundation**: Grounded in universal principles (entropy, evolution, emergence) rather than coding conventions
2. **Question-First Culture**: Challenges requirements systematically (Musk's method)
3. **Surgical Precision**: Only touch what must change (Karpathy's principles)
4. **Verified Execution**: Every step has a success criterion
5. **Transparent Uncertainty**: Never guess or beautify data

## Key Concepts

### First Principles Thinking
Strip away conventions and analogies. Derive solutions from fundamental truths (physics, math, logic).

### 5-Step Execution Priority
1. Question necessity
2. Delete non-essentials
3. Simplify what remains
4. Accelerate cycles
5. Automate last

### Data Integrity
- Never guess from unclear images
- Never beautify data for reports
- Always show calculation process
- Admit errors immediately

### Surgical Changes
- Each line change traces to user request
- Match existing style exactly
- Don't "improve" adjacent code
- Only clean up orphans from your changes

## Examples

**Before** (typical LLM behavior):
```
User: "Add validation to the login form"
Claude: [Adds validation + refactors form component + updates styles + adds unused error states]
```

**After** (with these directives):
```
User: "Add validation to the login form"
Claude: "I'll add email/password validation. Plan:
1. Add validation rules → Test with invalid inputs
2. Show error messages → Test error display
3. Prevent submission on invalid → Test submit blocking

Should I also handle edge cases like empty strings, or just basic format validation?"
[Makes only the requested changes, matching existing code style]
```

## Tradeoffs

These guidelines **bias toward caution over speed**. They are designed for:
- Non-trivial features
- Production systems
- Code with long-term maintenance
- Projects with multiple contributors

For simple typos or one-line fixes, use your judgment.

## Related Work

- **Karpathy's observations**: [Tweet thread on LLM coding mistakes](https://x.com/karpathy/status/2015883857489522876)
- **Musk's engineering methodology**: First principles thinking from SpaceX/Tesla manufacturing
- **BMAD-METHOD**: For full SDLC workflow (PM → Architect → Dev → QA)
- **claude-code-bmad-foundation**: Template that combines Karpathy + BMAD

## Contributing

This is a living document. If you find improvements:
1. Open an issue with your use case
2. Share what worked and what didn't
3. Suggest additions with clear reasoning

## License

MIT - Use freely, modify as needed, no attribution required.

## Acknowledgments

- **Andrej Karpathy**: For surfacing common LLM coding failure modes
- **Elon Musk**: For the 5-step engineering methodology
- **First principles thinkers**: For the cognitive foundation

---

**Not affiliated with Anthropic, OpenAI, or any AI company.**  
Just one developer's attempt to make Claude Code more systematically reliable.
