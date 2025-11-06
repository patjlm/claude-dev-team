# Claude Dev Team Plugin

A Claude Code plugin that provides **autonomous agent team management** with dynamic agent creation and skill recording capabilities.

## Overview

This plugin enables Claude Code to maintain a self-organizing team of specialized agents that adapt to your project's needs. Instead of manually creating and managing agents for every task, the plugin includes "seed agents" that:

- Analyze your project to determine what specialized agents are needed
- Create and configure agents dynamically in your project
- Record successful patterns and procedures as reusable skills
- Coordinate work across multiple agents efficiently
- Adapt the team structure as your project evolves

## Key Concepts

### Seed Agents (WHO manages the team)

Core agents included with the plugin that handle:
- **Team Orchestrator**: Manages agent lifecycle and task delegation
- **Skill Recorder**: Captures and documents successful patterns as skills
- **Team Architect**: Designs agent roles and responsibilities

### Dynamic Team (WHO does WHAT)

Project-specific agents created by seed agents based on:
- Your technology stack
- Development workflow patterns
- Recurring tasks and needs
- Team preferences

These agents are created in your project's `.claude/agents/` directory and can be version-controlled.

### Skills Repository (HOW things are done)

Reusable procedures and knowledge captured as Claude Code skills:
- Agent design patterns
- Multi-agent coordination techniques
- Project-specific best practices
- Successful workflow patterns

## Installation

### From Local Directory

```bash
# Navigate to your project
cd /path/to/your/project

# Install the plugin
claude /plugin install /path/to/claude-dev-team

# Enable the plugin
claude /plugin enable claude-dev-team
```

### From Marketplace (Coming Soon)

```bash
claude /plugin marketplace add https://github.com/patjlm/claude-dev-team
claude /plugin install claude-dev-team
```

## Usage

Once enabled, the seed agents will automatically:

1. **Analyze** your project structure and needs
2. **Propose** specialized agents for your workflow
3. **Create** agents in `.claude/agents/` with appropriate configurations
4. **Coordinate** multi-agent workflows for complex tasks
5. **Record** successful patterns as skills for future reuse

You can also explicitly invoke seed agents:

```bash
# Ask the team orchestrator to analyze needs
"What agents would be helpful for this project?"

# Request skill recording
"Record the approach we just used as a skill"

# Get team architecture recommendations
"How should we organize agents for this microservices project?"
```

## Benefits

### Context Efficiency
Delegate specialized work to focused agents with minimal context, keeping the main conversation lightweight.

### Parallel Execution
Enable multiple agents to work concurrently on different aspects of complex tasks.

### Knowledge Persistence
Capture institutional knowledge as skills that persist across sessions and projects.

### Dynamic Adaptation
Team structure evolves with your project - no manual agent management required.

### Best Practice Compliance
Follow current Claude Code patterns for agents, skills, and workflows automatically.

## Project Structure

```
claude-dev-team/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata
├── agents/                   # Seed agents
│   ├── team-orchestrator/
│   ├── skill-recorder/
│   └── team-architect/
├── skills/                   # Reusable skills
│   ├── agent-design/
│   ├── skill-creation/
│   └── team-coordination/
└── README.md
```

## Development

This plugin is in early development (v0.1.0). Contributions welcome!

### Testing Locally

1. Clone this repository
2. Install in a test project: `claude /plugin install /path/to/claude-dev-team`
3. Enable: `claude /plugin enable claude-dev-team`
4. Verify seed agents: `"Show me available agents"`

### Architecture

See [CLAUDE.md](./CLAUDE.md) for detailed architecture and development guidance.

## Documentation

- [Claude Code Plugin Docs](https://code.claude.com/docs/en/plugins.md)
- [Sub-agents Guide](https://code.claude.com/docs/en/sub-agents.md)
- [Skills Guide](https://code.claude.com/docs/en/skills.md)

## License

MIT

## Author

patjlm
