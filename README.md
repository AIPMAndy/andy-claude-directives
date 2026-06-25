# 👉 [中文文档 Chinese README](./README_CN.md)

---

# AgentCorePrompt - Core Operating Directives for AI Agents

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub stars](https://img.shields.io/github/stars/AIPMAndy/AgentCorePrompt?style=social)](https://github.com/AIPMAndy/AgentCorePrompt/stargazers)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

> **📖 [中文完整文档请点击这里 | Click here for Chinese documentation](./README_CN.md)**

Universal behavioral guidelines for AI coding agents (Claude Code, Codex, Cursor, etc.) that combines fundamental cognitive axioms, Musk's engineering methodology, and Karpathy's coding principles to maximize execution quality and minimize common LLM mistakes.

**Works with: Claude Code, OpenAI Codex, Cursor, and any AI agent that reads project instructions.**

**[中文](./README_CN.md) | [English](./README.md)**

## What This Is

A **universal configuration file** designed to make AI coding agents:
- Think from first principles instead of surface analogies
- Question requirements before implementing
- Write minimal, surgical code changes
- Verify results systematically
- Handle uncertainty transparently

**Compatible with:**
- 🤖 **Claude Code** (via `CLAUDE.md`)
- 🔧 **OpenAI Codex** (via `.cursorrules` or system prompt)
- ⚡ **Cursor** (via `.cursorrules`)
- 🎯 **Any AI agent** that reads project instructions

Built on three pillars:
1. **9 Cognitive Axioms** (entropy law, reductionism, probabilistic uncertainty, etc.)
2. **Musk's 5-Step Engineering Method** (question → delete → simplify → accelerate → automate)
3. **Karpathy's 4 Coding Principles** (think before coding, simplicity first, surgical changes, goal-driven execution)

## Who This Is For

**Use this if you:**
- Want AI agents to think more systematically and make fewer mistakes
- Need transparent reasoning and explicit uncertainty handling
- Value minimal, surgical code changes over "improvements"
- Want goal-driven execution with verifiable checkpoints
- Work on projects where data integrity is critical

**This is NOT:**
- A project template (no scaffolding, no CI/CD, no tech stack)
- An application framework
- A replacement for domain-specific instructions

## Quick Start

```bash
# For Claude Code
curl -o CLAUDE.md https://raw.githubusercontent.com/AIPMAndy/AgentCorePrompt/main/CLAUDE.md

# For Cursor / Codex
curl -o .cursorrules https://raw.githubusercontent.com/AIPMAndy/AgentCorePrompt/main/CLAUDE.md

# Or browse templates for specific use cases
curl -O https://raw.githubusercontent.com/AIPMAndy/AgentCorePrompt/main/TEMPLATES.md
```

## How to Use

### For Claude Code
Copy `CLAUDE.md` to your project root:
```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/AIPMAndy/AgentCorePrompt/main/CLAUDE.md
```
Claude Code will automatically load it.

### For Cursor / Codex
Copy as `.cursorrules`:
```bash
curl -o .cursorrules https://raw.githubusercontent.com/AIPMAndy/AgentCorePrompt/main/CLAUDE.md
```

### For Other AI Agents
Copy the content and adapt to your agent's configuration format (system prompt, instruction file, etc.).

### Customize
Edit the file to add your:
- Tech stack and locked dependencies
- Project-specific rules and conventions
- Team workflow and git practices
- Domain knowledge and edge cases

The file is modular - keep what fits your workflow, remove what doesn't.

## Documentation

- 📖 **[Templates](./TEMPLATES.md)** - 6 pre-configured templates for different use cases
- 💡 **[Examples](./EXAMPLES.md)** - Before/after comparisons showing real behavior changes
- 🇨🇳 **[中文文档](./README_CN.md)** - Complete Chinese documentation

## What Makes This Different

Most prompt engineering focuses on "how to code." This focuses on **"how to think"** before coding:

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
AI: [Adds validation + refactors form + updates styles + adds unused error states]
```

**After** (with AgentCorePrompt):
```
User: "Add validation to the login form"
AI: "I'll add email/password validation. Plan:
1. Add validation rules → Test with invalid inputs
2. Show error messages → Test error display
3. Prevent submission on invalid → Test submit blocking

Should I also handle edge cases like empty strings, or just basic format validation?"
[Makes only the requested changes, matching existing code style]
```

See [EXAMPLES.md](./EXAMPLES.md) for 5 detailed before/after comparisons.

## Tradeoffs

These guidelines **bias toward caution over speed**. They are designed for:
- Non-trivial features
- Production systems
- Code with long-term maintenance
- Projects with multiple contributors

For simple typos or one-line fixes, use your judgment.

## Star History

If this helped you, consider giving it a star ⭐

[![Star History Chart](https://api.star-history.com/svg?repos=AIPMAndy/AgentCorePrompt&type=Date)](https://star-history.com/#AIPMAndy/AgentCorePrompt&Date)

## Community

- **Share your success story**: [Use this template](./.github/ISSUE_TEMPLATE/success_story.md)
- **Report issues**: [Bug report template](./.github/ISSUE_TEMPLATE/bug_report.md)
- **Suggest improvements**: [Improvement template](./.github/ISSUE_TEMPLATE/improvement.md)

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

**Not affiliated with Anthropic, OpenAI, Cursor, or any AI company.**  
Just one developer's attempt to make AI coding agents more systematically reliable.

## Support

If you find this valuable:
- ⭐ Star the repo
- 🐦 Share on [Twitter/X](https://twitter.com/intent/tweet?text=Check%20out%20AgentCorePrompt%20-%20Universal%20directives%20for%20AI%20coding%20agents%20(Claude%2C%20Codex%2C%20Cursor)%20-%20Combines%20cognitive%20axioms%2C%20Musk%27s%20methodology%2C%20and%20Karpathy%27s%20principles&url=https://github.com/AIPMAndy/AgentCorePrompt)
- 💬 Share your success story in Issues
- 🤝 Contribute improvements via PR
