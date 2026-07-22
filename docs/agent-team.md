# Agent team

Mona's Project Pulse dashboard is built using a specialized four-agent team orchestrated through GitHub Copilot CLI in a Codespace. Each agent is purpose-built with specific capabilities and constraints to deliver high-quality, modular work.

## Agents

### Orchestrator
- **Model:** Claude Opus 4.7 (copilot)
- **Location:** [.github/agents/orchestrator.agent.md](.github/agents/orchestrator.agent.md)
- **Responsibility:** Coordinates the Planner, Coder, and Designer agents. Breaks down complex requests into phases, manages task dependencies, runs work in parallel when safe, and verifies integrated results.

### Planner
- **Model:** Claude Opus 4.7 (copilot)
- **Location:** [.github/agents/planner.agent.md](.github/agents/planner.agent.md)
- **Responsibility:** Creates implementation strategies and technical plans. Researches the codebase, identifies dependencies and edge cases, and produces ordered implementation steps with file assignments and parallel/sequential work guidance.

### Coder
- **Model:** GPT-5.5 (copilot)
- **Location:** [.github/agents/coder.agent.md](.github/agents/coder.agent.md)
- **Responsibility:** Implements code-oriented tasks with clear structure, explicit errors, and testable behavior. Works within assigned file scopes, creates launch configurations, and maintains deterministic, maintainable code patterns.

### Designer
- **Model:** Gemini 3.1 Pro (copilot)
- **Location:** [.github/agents/designer.agent.md](.github/agents/designer.agent.md)
- **Responsibility:** Handles UI/UX, accessibility, information hierarchy, interaction flow, and visual design. Creates a polished dashboard with visible project cards, status badges, responsive layout, and clear visual affordances.

## Orchestration

All agents work under GitHub Copilot CLI in a Codespace environment, with the learner controlling git operations through Copilot CLI prompts. This setup enables specialized expertise to be applied precisely where needed while maintaining a clear separation of concerns.
