# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Claude Code plugin that provides a **fully autonomous and dynamically configured team of Claude Code agents**. The plugin enables projects to maintain a self-organizing team of specialized agents that adapt to project needs, record learnings as skills, and follow best practices from the Claude Code ecosystem.

### Core Concept

The plugin implements a hierarchical agent system:
- **Seed Agents**: A small set of core agents responsible for team management, configuration, growth, and adaptation
- **Dynamic Team**: Agents created/configured by seed agents to handle specific project needs (WHO does WHAT)
- **Skills Repository**: Recorded knowledge and procedures (HOW things are done) that persist across sessions

### Goals

1. **Context Efficiency**: Limit context size on the main agent by delegating to specialized sub-agents
2. **Parallelization**: Enable concurrent work through multiple agents
3. **Dynamic Adaptation**: Create, modify, and retire agents based on evolving project needs
4. **Knowledge Capture**: Record best practices and procedures as reusable skills
5. **Best Practice Compliance**: Follow up-to-date Claude Code patterns and conventions

## Architecture

### Plugin Structure

```
claude-dev-team/
├── .claude-plugin/
│   └── plugin.json           # Plugin manifest
├── agents/                   # Seed agents (core team managers)
│   ├── team-orchestrator/    # Manages agent lifecycle and delegation
│   ├── skill-recorder/       # Captures and documents skills
│   └── team-architect/       # Designs agent roles and responsibilities
├── skills/                   # Reusable skills (HOW)
│   ├── agent-design/         # How to design effective agents
│   ├── skill-creation/       # How to create and document skills
│   └── team-coordination/    # How to coordinate multi-agent work
├── commands/                 # Custom slash commands (optional)
└── hooks/                    # Event handlers for automation (optional)
```

### Key Components

#### Seed Agents (agents/)
These are the foundational agents that come with the plugin. They are responsible for:
- Analyzing project requirements to determine needed agent roles
- Creating/configuring new agents dynamically in the project's `.claude/agents/` directory
- Recording successful patterns and procedures as skills
- Coordinating work across multiple agents
- Adapting the team structure as the project evolves

#### Skills (skills/)
Skills capture procedural knowledge that can be invoked automatically by Claude. They document:
- How to design effective sub-agents for specific purposes
- How to coordinate multi-agent workflows
- How to capture and document learnings
- Project-specific patterns and best practices (recorded during usage)

#### Dynamic Team (created at runtime in project's `.claude/agents/`)
When this plugin is enabled in a project, the seed agents will create project-specific agents in the project's `.claude/agents/` directory based on:
- Project technology stack
- Development workflow patterns
- Team preferences
- Recurring tasks and needs

## Development Workflow

### Testing the Plugin Locally

1. Install the plugin in test mode:
   ```bash
   # From your test project directory
   claude /plugin install /path/to/claude-dev-team
   ```

2. Enable the plugin:
   ```bash
   claude /plugin enable claude-dev-team
   ```

3. Verify seed agents are available:
   ```bash
   # List available agents
   claude "Show me available agents"
   ```

### Modifying Agents

Agents are defined in `agents/*/AGENT.md` files with frontmatter:
```yaml
---
name: agent-name
description: When to use this agent (max 1024 chars)
tools: [optional tool restrictions]
model: sonnet|opus|haiku (optional)
---

# Agent System Prompt
Detailed instructions for the agent...
```

### Creating Skills

Skills are defined in `skills/*/SKILL.md` files:
```yaml
---
name: skill-name
description: What this skill does and when to use it
allowed-tools: [optional tool restrictions]
---

# Skill Documentation
Instructions and examples...
```

## Reference Documentation

### Claude Code Documentation
- [Plugin Development](https://code.claude.com/docs/en/plugins.md)
- [Plugin Reference](https://code.claude.com/docs/en/plugins-reference.md)
- [Sub-agents Guide](https://code.claude.com/docs/en/sub-agents.md)
- [Skills Guide](https://code.claude.com/docs/en/skills.md)

### Key Concepts

**Sub-agents**: Specialized AI assistants with dedicated context windows, configured tools, and specific system prompts. They can be automatically invoked by Claude or explicitly called.

**Skills**: Modular capabilities that extend Claude's functionality. Claude autonomously decides when to invoke skills based on their descriptions.

**Plugins**: Shareable packages that can provide commands, agents, skills, hooks, and MCP server configurations.

## Design Principles

1. **Agent Specialization**: Each agent should have a clear, focused purpose
2. **Skill Modularity**: Skills should capture single, reusable procedures
3. **Dynamic Over Static**: Prefer runtime agent creation over pre-defined agents
4. **Context Awareness**: Use agent descriptions to guide automatic invocation
5. **Knowledge Persistence**: Capture successful patterns as skills for reuse
6. **Parallel Execution**: Design agents to work independently when possible

## Plugin Metadata

- **Name**: claude-dev-team
- **Purpose**: Autonomous agent team management and skill recording
- **Components**: Seed agents, skill templates, team coordination patterns
- **Target Users**: Projects wanting self-organizing AI assistance
