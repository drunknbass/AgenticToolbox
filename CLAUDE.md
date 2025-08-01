# AgenticToolbox

## Overview

This repository serves as a curated collection of agentic snippets, patterns, and helpers designed to accelerate development workflows. We're building a comprehensive library of specialized AI agents that can be proactively invoked to handle specific development tasks with expertise and consistency.

## Purpose

The AgenticToolbox aims to:
- **Standardize Excellence**: Maintain high-quality, production-ready code patterns across all agents
- **Accelerate Development**: Provide instant access to specialized expertise for common development scenarios
- **Promote Best Practices**: Embed industry standards and architectural patterns into every agent
- **Enable Reusability**: Create modular, composable agents that work seamlessly together

## Agent Categories

### Architecture & Design
- `swiftui-architect`: iOS/macOS UI development with SwiftUI best practices
- `swiftui-3d-designer`: Specialized 3D interface development (Spline, RealityKit, SceneKit)
- `backend-api-architect`: RESTful and GraphQL API design patterns
- `nextjs-project-bootstrapper`: Rapid Next.js project initialization

### Quality & Maintenance
- `code-refactoring-architect`: Code optimization and modernization
- `qa-test-engineer`: Comprehensive testing strategies and implementation
- `security-audit-specialist`: Security vulnerability assessment and remediation

### Orchestration
- `project-orchestrator`: Multi-agent coordination for complex projects

## Best Practices

### 1. No Attribution Policy
- **NO Claude attribution in commits**: All commits should be clean without AI attribution
- **NO Claude attribution in PRs**: Pull requests should not mention AI assistance
- This is enforced via `.claude/settings.json` configuration

### 2. Agent Design Principles
- **Single Responsibility**: Each agent focuses on one domain of expertise
- **Self-Contained**: Agents include all necessary context and examples
- **Production-Ready**: Code examples should be immediately usable
- **Tool-Aware**: Agents specify which tools they need (Read, Write, Grep, etc.)

### 3. Code Quality Standards
- **Type Safety**: Prefer strongly-typed languages and strict configurations
- **Modern Patterns**: Use current best practices and latest stable APIs
- **Performance First**: Consider performance implications in all suggestions
- **Security by Default**: Embed security considerations into every recommendation

### 4. Documentation Requirements
- **Clear Mission Statement**: Each agent must define its purpose clearly
- **Practical Examples**: Include working code snippets and templates
- **Decision Rationale**: Explain the "why" behind recommendations
- **Version Awareness**: Specify language/framework versions explicitly

## Usage Guidelines

1. **Agent Selection**: Choose the most specific agent for your task
2. **Combining Agents**: Use multiple agents for complex, multi-faceted projects
3. **Customization**: Adapt agent templates to your specific needs
4. **Feedback Loop**: Continuously improve agents based on real-world usage

## Contributing

When adding new agents:
1. Follow the existing agent template structure
2. Include comprehensive examples and edge cases
3. Test all code snippets for correctness
4. Document any external dependencies or requirements
5. Ensure the agent name clearly indicates its specialty

## Repository Structure

```
AgenticToolbox/
├── agents/                 # Specialized AI agent definitions
│   ├── *.md               # Individual agent files
├── integrations/          # Integration examples and templates
├── .claude/               # Claude-specific configuration
│   └── settings.json      # Project settings (gitignored)
├── .gitignore            # Comprehensive ignore patterns
├── CLAUDE.md             # This file
└── README.md             # Public repository documentation
```

## Privacy & Security

- All Claude settings are gitignored to prevent exposure of preferences
- Secrets and credentials are excluded via comprehensive .gitignore
- No sensitive information should be committed to this repository

---

*This toolbox is actively maintained and expanded based on development needs and community feedback.*