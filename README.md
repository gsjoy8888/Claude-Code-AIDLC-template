# Claude Code AIDLC Workflow Template

> Adapted from [Kiro-AIDLC-workflow-template](https://github.com/FelixFeli/Kiro-AIDLC-workflow-template) for use with **Claude Code**.

AI-DLC (AI-Driven Development Life Cycle) is an intelligent software development methodology that guides you through structured development phases from concept to deployment. For more details, read the [AI-DLC Blog](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) and the [methodology paper](https://prod.d13rzhkk8cj2z0.amplifyapp.com/).

## Quick Start

```bash
# 1. Clone this repo
git clone https://github.com/gsjoy8888/Claude-Code-AIDLC-template.git
cd Claude-Code-AIDLC-template

# 2. Start Claude Code
claude

# 3. Begin your project
Using AI-DLC, [describe your project requirements]

# Or use the slash command
/aidlc [describe your project requirements]
```

## What's Included

```
├── CLAUDE.md                    # Core AI-DLC workflow (auto-loaded by Claude Code)
├── .aidlc-rule-details/         # Detailed rules and phase guides
│   ├── common/                  # Shared rules (validation, questions, etc.)
│   ├── inception/               # Inception phase rules
│   ├── construction/            # Construction phase rules
│   ├── operations/              # Operations phase rules (placeholder)
│   └── extensions/              # Cross-cutting constraints (security, etc.)
├── .claude/
│   ├── commands/
│   │   └── aidlc.md             # /aidlc slash command
│   └── settings.json            # Permission settings for workshop
├── .kiro/                       # Original Kiro files (kept for reference)
│   ├── steering/
│   └── aws-aidlc-rule-details/
└── aidlc-docs/                  # Generated artifacts (created during workflow)
```

## How It Works

### AI-DLC Phases

```
🔵 Inception Phase          → What to build and why
   ├── Workspace Detection   (always)
   ├── Reverse Engineering   (brownfield only)
   ├── Requirements Analysis (always, adaptive depth)
   ├── User Stories          (conditional)
   ├── Workflow Planning     (always)
   ├── Application Design    (conditional)
   └── Unit Generation       (conditional)

🟢 Construction Phase       → How to build it
   ├── Per-Unit Loop:
   │   ├── Functional Design    (conditional)
   │   ├── NFR Requirements     (conditional)
   │   ├── NFR Design           (conditional)
   │   ├── Infrastructure Design(conditional)
   │   └── Code Generation      (always)
   └── Build & Test            (always)

🟡 Operations Phase         → How to deploy and run (future)
```

### Key Differences from Kiro Version

| Feature | Kiro | Claude Code |
|---------|------|-------------|
| Workflow file | `.kiro/steering/core-workflow.md` | `CLAUDE.md` (project root) |
| Rule details | `.kiro/aws-aidlc-rule-details/` | `.aidlc-rule-details/` |
| Slash commands | Built-in | `.claude/commands/aidlc.md` |
| Stage approval | Kiro UI | Conversational confirmation |
| File operations | Kiro editor | Claude Code Write/Edit tools |

### Adaptive Workflow

- **Workflow adapts to work**: AI assesses which phases are needed
- **Transparent planning**: Always shows execution plan before starting
- **User control**: You can request to include/exclude phases
- **Quality focus**: Complex changes get full treatment, simple ones stay efficient

## Workshop Usage

### Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed
- AWS Bedrock configured (or Anthropic API key)
- Basic understanding of your project requirements

### Recommended Workshop Flow

```
1. Environment Setup (15 min)
   - Confirm Claude Code is installed
   - Clone this template repo

2. AI-DLC Concepts (15 min)
   - Three phases: Inception → Construction → Operations
   - How CLAUDE.md drives the workflow

3. Hands-on Lab (60 min)
   - Type "Using AI-DLC, [your project]"
   - Follow the guided workflow
   - Review and approve each phase

4. Review & Discussion (15 min)
   - Explore aidlc-docs/ generated artifacts
   - Review audit.md for decision history
```

### Example Prompts

```
Using AI-DLC, create a task management REST API with user authentication

Using AI-DLC, add real-time notification to my existing chat app

Using AI-DLC, investigate and fix performance issues in the user dashboard
```

## Generated Artifacts

All AI-DLC artifacts are organized in `aidlc-docs/`:

```
aidlc-docs/
├── inception/
│   ├── plans/
│   ├── reverse-engineering/
│   ├── requirements/
│   ├── user-stories/
│   └── application-design/
├── construction/
│   ├── plans/
│   ├── {unit-name}/
│   │   ├── functional-design/
│   │   ├── nfr-requirements/
│   │   ├── nfr-design/
│   │   ├── infrastructure-design/
│   │   └── code/
│   └── build-and-test/
├── operations/
├── aidlc-state.md
└── audit.md
```

**Important**: Application code is always generated at the workspace root, not inside `aidlc-docs/`.

## Tips

- **Be specific**: Provide clear, detailed requirements in your initial request
- **Review carefully**: Always review and approve each phase before continuing
- **Ask questions**: Use the structured Q&A format for clarifications
- **Track progress**: Monitor workflow status in `aidlc-state.md`
- **Stay in control**: You can request changes or skip phases as needed

## Credits

- Original template: [FelixFeli/Kiro-AIDLC-workflow-template](https://github.com/FelixFeli/Kiro-AIDLC-workflow-template)
- AI-DLC Methodology: [AWS DevOps Blog](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)

## License

This template is licensed under MIT-0. See [LICENSE](LICENSE) for details.
