# AgenticToolbox

A curated collection of specialized AI agents designed to accelerate software development workflows.

## Overview

AgenticToolbox provides ready-to-use AI agent configurations that can be proactively invoked for specific development tasks. Each agent is crafted with deep expertise in its domain, following best practices and modern patterns.

## Available Agents

### Swift & iOS Development
- **[swiftui-architect](agents/swiftui-architect.md)** - Modern SwiftUI development with iOS 18+ best practices
- **[swiftui-3d-designer](agents/swiftui-3d-designer.md)** - 3D interface specialist for Spline, RealityKit, SceneKit integration
- **[swift-tca-architect](agents/swift-tca-architect.md)** - Point-Free's Composable Architecture expert with test-first approach

### Backend & API
- **[backend-api-architect](agents/backend-api-architect.md)** - RESTful and GraphQL API design patterns
- **[nextjs-project-bootstrapper](agents/nextjs-project-bootstrapper.md)** - Rapid Next.js project initialization

### Quality & Maintenance
- **[code-refactoring-architect](agents/code-refactoring-architect.md)** - Code optimization and modernization specialist
- **[qa-test-engineer](agents/qa-test-engineer.md)** - Comprehensive testing strategies and implementation
- **[security-audit-specialist](agents/security-audit-specialist.md)** - Security vulnerability assessment and remediation

### Orchestration
- **[project-orchestrator](agents/project-orchestrator.md)** - Multi-agent coordination for complex projects

## Quick Start

1. Clone this repository
2. Browse the `agents/` directory to find specialized agents
3. Use agent definitions with AI assistants that support custom instructions
4. Adapt templates to your specific project needs

## Agent Structure

Each agent follows a consistent structure:
```yaml
---
name: agent-name
description: Clear description of agent's expertise
tools: List of required tools (Read, Write, Grep, etc.)
---

## Mission
Agent's primary objectives and focus areas

## Core Patterns
Key patterns, APIs, and best practices

## Templates
Ready-to-use code templates and examples
```

## Contributing

When adding new agents:
1. Use descriptive names that clearly indicate the specialty
2. Include comprehensive examples and edge cases
3. Test all code snippets for correctness
4. Document dependencies and version requirements
5. Follow the existing agent template structure

## Best Practices

- **Single Responsibility**: Each agent focuses on one domain
- **Production Ready**: All code examples should be immediately usable
- **Modern Patterns**: Use current best practices and latest stable APIs
- **Test Coverage**: Include testing strategies and examples

## License

This repository is available for use in development projects. See individual agent files for specific library and framework licenses.

---

*For detailed repository guidelines and contribution standards, see [CLAUDE.md](CLAUDE.md)*