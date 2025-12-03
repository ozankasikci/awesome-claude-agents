# Awesome Claude Agents

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

> A curated list of Claude Code agents, subagents, skills, frameworks, and resources for building AI-powered development workflows.

Claude agents are specialized AI assistants that extend Claude's capabilities for specific tasks. This repository catalogs the best community-created agents, official resources, and tools to supercharge your development workflow.

---

## Contents

- [What are Claude Agents?](#what-are-claude-agents)
- [Getting Started](#getting-started)
- [Agent Collections](#agent-collections)
- [Agents by Category](#agents-by-category)
  - [Core Development](#core-development)
  - [Language Specialists](#language-specialists)
  - [Infrastructure & DevOps](#infrastructure--devops)
  - [Quality & Security](#quality--security)
  - [Data & AI](#data--ai)
  - [Developer Experience](#developer-experience)
  - [Business & Product](#business--product)
  - [Orchestration & Meta](#orchestration--meta)
- [Claude Skills](#claude-skills)
- [Frameworks & Tools](#frameworks--tools)
- [Workflow Patterns](#workflow-patterns)
- [Creating Your Own Agent](#creating-your-own-agent)
- [Best Practices](#best-practices)
- [Community Resources](#community-resources)
- [Contributing](#contributing)

---

## What are Claude Agents?

**Claude Agents** (also called subagents) are specialized AI assistants that can be invoked within Claude Code to handle specific types of tasks. They were introduced by Anthropic in July 2025 to address the critical problem of "context pollution."

### Key Benefits

- **Isolated Context Windows** - Each subagent operates in its own context, keeping the main conversation focused
- **Specialization** - Custom system prompts and focused capabilities for specific domains
- **Parallelization** - Spin up multiple subagents to work on different tasks simultaneously
- **Team Sharing** - Share agents with your team for consistent workflows
- **Tool Permissions** - Each subagent can have different tool access levels

### Types of Agents

| Type | Description | Location |
|------|-------------|----------|
| **Built-in Subagents** | Pre-configured agents like `Explore` (codebase analysis) and `Plan` (planning mode) | System |
| **User Subagents** | Personal agents available across all projects | `~/.claude/agents/` |
| **Project Subagents** | Team-shared agents specific to a project | `.claude/agents/` |
| **Skills** | Specialized folders with instructions, scripts, and resources | `~/.claude/skills/` or `.claude/skills/` |

---

## Getting Started

### Installation

1. **Create the agents directory:**
   ```bash
   mkdir -p ~/.claude/agents
   ```

2. **Add an agent file** (e.g., `~/.claude/agents/code-reviewer.md`):
   ```markdown
   ---
   name: code-reviewer
   description: Expert code review specialist. Use PROACTIVELY after code changes.
   tools: Read, Grep, Glob, Bash
   model: inherit
   ---

   You are a senior code reviewer with 15+ years of experience.

   When invoked:
   1. Run `git diff` to identify modified files
   2. Analyze changed code for security, performance, and maintainability
   3. Provide actionable feedback with specific line references
   4. Suggest improvements with code examples
   ```

3. **Use the agent in Claude Code:**
   ```
   "Use the code-reviewer to check my recent changes"
   ```

### Agent File Format

```markdown
---
name: agent-name                    # Required: unique identifier
description: When to use this agent # Required: triggers automatic invocation
tools: Tool1, Tool2, Tool3          # Optional: defaults to all tools
model: sonnet | opus | haiku | inherit  # Optional: defaults to sonnet
permissionMode: default             # Optional: permission handling
skills: skill1, skill2              # Optional: auto-load specific skills
---

Your agent's system prompt goes here.
Include role definition, capabilities, and specific instructions.
```

### Quick Clone Collections

```bash
# VoltAgent's 100+ production agents
git clone https://github.com/VoltAgent/awesome-claude-code-subagents.git ~/.claude/agents/voltagent

# wshobson's 48 production-ready specialists
git clone https://github.com/wshobson/agents.git ~/.claude/agents/wshobson

# 0xfurai's comprehensive collection
git clone https://github.com/0xfurai/claude-code-subagents.git ~/.claude/agents/0xfurai
```

---

## Agent Collections

### Production-Ready Collections

| Collection | Agents | Description | Link |
|------------|--------|-------------|------|
| **VoltAgent/awesome-claude-code-subagents** | 100+ | Full-stack development, DevOps, data science, business operations | [GitHub](https://github.com/VoltAgent/awesome-claude-code-subagents) |
| **wshobson/agents** | 48 | Production-ready specialists with orchestration patterns | [GitHub](https://github.com/wshobson/agents) |
| **0xfurai/claude-code-subagents** | 100+ | Uniform prompt formatting, multi-language support | [GitHub](https://github.com/0xfurai/claude-code-subagents) |
| **vijaythecoder/awesome-claude-agents** | 26 | AI development team with tech lead and domain experts | [GitHub](https://github.com/vijaythecoder/awesome-claude-agents) |
| **davepoon/claude-code-subagents-collection** | 36 | Auto-delegation and best practices guide | [GitHub](https://github.com/davepoon/claude-code-subagents-collection) |
| **charles-adedotun/claude-code-sub-agents** | 30+ | Full ecosystem mapped to development workflow stages | [GitHub](https://github.com/charles-adedotun/claude-code-sub-agents) |

### Specialized Collections

| Collection | Focus | Link |
|------------|-------|------|
| **iannuttall/claude-agents** | Refactoring, content writing, frontend design, PRD creation | [GitHub](https://github.com/iannuttall/claude-agents) |
| **zhsama/claude-sub-agent** | Spec-driven development pipeline with quality gates | [GitHub](https://github.com/zhsama/claude-sub-agent) |
| **lst97/claude-code-sub-agents** | Full-stack development specialists | [GitHub](https://github.com/lst97/claude-code-sub-agents) |

---

## Agents by Category

### Core Development

Essential agents for everyday coding tasks:

| Agent | Description | Recommended Tools |
|-------|-------------|-------------------|
| **frontend-developer** | React/Vue/Angular components, state management, UI optimization | Read, Write, Edit, Bash, Glob |
| **backend-developer** | Server-side logic, API implementation, database integration | Read, Write, Edit, Bash, Grep |
| **fullstack-developer** | End-to-end feature development | All tools |
| **api-designer** | RESTful/GraphQL API design, OpenAPI specs | Read, Write, Edit, Glob |
| **ui-designer** | Component design, design systems, visual aesthetics | Read, Write, Edit |
| **mobile-developer** | iOS/Android app development | Read, Write, Edit, Bash |
| **microservices-architect** | Distributed system design, service decomposition | Read, Grep, Glob, Bash |
| **graphql-architect** | Schema design, resolver optimization | Read, Write, Edit, Grep |
| **websocket-engineer** | Real-time communication, event-driven architecture | Read, Write, Edit, Bash |

### Language Specialists

Deep expertise across programming languages:

| Agent | Languages/Frameworks |
|-------|---------------------|
| **python-pro** | Python, FastAPI, Django, Flask |
| **typescript-pro** | TypeScript, Node.js, Deno |
| **javascript-pro** | JavaScript, ES6+, npm ecosystem |
| **react-specialist** | React, Redux, Next.js |
| **vue-expert** | Vue 3, Vuex, Nuxt |
| **angular-architect** | Angular, RxJS, NgRx |
| **golang-pro** | Go, Gin, Echo |
| **rust-engineer** | Rust, Cargo, async/await |
| **java-architect** | Java, Spring Boot, Maven |
| **csharp-developer** | C#, .NET Core, ASP.NET |
| **swift-expert** | Swift, SwiftUI, iOS |
| **kotlin-specialist** | Kotlin, Android, Coroutines |
| **php-pro** | PHP, Laravel, Symfony |
| **rails-expert** | Ruby on Rails, ActiveRecord |
| **flutter-expert** | Flutter, Dart, cross-platform |

### Infrastructure & DevOps

DevOps and deployment specialists:

| Agent | Description | Key Skills |
|-------|-------------|------------|
| **devops-engineer** | CI/CD pipelines, automation, infrastructure | Jenkins, GitHub Actions, GitLab CI |
| **cloud-architect** | Multi-cloud design, cost optimization | AWS, GCP, Azure |
| **kubernetes-specialist** | Container orchestration, Helm charts | K8s, Docker, Istio |
| **terraform-engineer** | Infrastructure as Code, state management | Terraform, Pulumi |
| **platform-engineer** | Internal developer platforms, tooling | Backstage, ArgoCD |
| **sre-engineer** | Reliability, SLOs, incident response | Prometheus, Grafana |
| **database-administrator** | Query optimization, replication, backup | PostgreSQL, MySQL, MongoDB |
| **network-engineer** | Network design, security, DNS | VPC, Load Balancers, CDN |
| **security-engineer** | Security architecture, threat modeling | IAM, encryption, compliance |

### Quality & Security

Testing and security experts:

| Agent | Description | Permissions |
|-------|-------------|-------------|
| **code-reviewer** | Code quality, style, maintainability | Read, Grep, Glob (read-only) |
| **security-auditor** | Vulnerability scanning, OWASP compliance | Read, Grep, Glob (read-only) |
| **qa-expert** | Test strategy, coverage analysis | Read, Write, Edit, Bash |
| **test-automator** | Unit/integration/e2e test generation | Read, Write, Edit, Bash |
| **performance-engineer** | Profiling, optimization, benchmarking | Read, Bash, Grep |
| **accessibility-tester** | WCAG compliance, a11y testing | Read, Grep, Glob |
| **penetration-tester** | Security testing, exploit analysis | Read, Grep, Bash |
| **debugger** | Error investigation, root cause analysis | Read, Grep, Glob, Bash |
| **architect-reviewer** | Design review, pattern validation | Read, Grep, Glob |

### Data & AI

Data engineering and ML specialists:

| Agent | Description |
|-------|-------------|
| **data-scientist** | Statistical analysis, ML modeling, visualization |
| **data-engineer** | ETL pipelines, data warehousing, Spark |
| **ml-engineer** | Model training, deployment, MLOps |
| **llm-architect** | LLM integration, prompt engineering, RAG |
| **nlp-engineer** | Text processing, transformers, embeddings |
| **data-analyst** | SQL, BI tools, reporting |
| **database-optimizer** | Query tuning, indexing, schema design |
| **mlops-engineer** | Model versioning, monitoring, serving |
| **prompt-engineer** | Prompt optimization, few-shot learning |

### Developer Experience

Tooling and productivity:

| Agent | Description |
|-------|-------------|
| **documentation-engineer** | API docs, README files, technical writing |
| **refactoring-specialist** | Code modernization, pattern migration |
| **legacy-modernizer** | Legacy system updates, tech debt reduction |
| **cli-developer** | Command-line tool development |
| **build-engineer** | Build systems, bundlers, compilation |
| **dependency-manager** | Package updates, security patches |
| **git-workflow-manager** | Branching strategies, PR management |
| **dx-optimizer** | Developer experience improvements |
| **mcp-developer** | Model Context Protocol server development |

### Business & Product

Product and business specialists:

| Agent | Description |
|-------|-------------|
| **product-manager** | Feature specs, roadmaps, prioritization |
| **technical-writer** | User documentation, tutorials, guides |
| **business-analyst** | Requirements gathering, process mapping |
| **project-manager** | Sprint planning, task tracking |
| **ux-researcher** | User research, journey maps, testing |
| **content-marketer** | Blog posts, marketing copy |
| **scrum-master** | Agile ceremonies, team facilitation |

### Orchestration & Meta

Multi-agent coordination:

| Agent | Description |
|-------|-------------|
| **multi-agent-coordinator** | Task distribution across multiple agents |
| **workflow-orchestrator** | Complex workflow management |
| **context-manager** | Context optimization, memory management |
| **task-distributor** | Work parallelization, load balancing |
| **knowledge-synthesizer** | Information aggregation across agents |

---

## Claude Skills

Skills are specialized folders containing instructions, scripts, and resources that Claude dynamically discovers and loads.

### Official Skills

| Skill | Description |
|-------|-------------|
| **pdf** | Extract text/tables, create PDFs, merge/split documents |
| **xlsx** | Create and analyze Excel spreadsheets with formulas |
| **docx** | Create and edit Word documents with formatting |
| **pptx** | Create and edit PowerPoint presentations |
| **artifacts-builder** | Build HTML artifacts using React, Tailwind, shadcn/ui |
| **mcp-builder** | Guide for creating MCP servers |
| **webapp-testing** | Test web applications using Playwright |
| **skill-creator** | Interactive tool for creating new skills |

### Community Skills

| Skill | Description | Link |
|-------|-------------|------|
| **obra/superpowers** | 20+ battle-tested skills including debugging, brainstorming | [GitHub](https://github.com/obra/superpowers) |
| **ios-simulator-skill** | iOS app building and testing automation | Community |
| **playwright-skill** | Browser automation and testing | Community |
| **claude-d3js-skill** | D3.js data visualizations | Community |
| **web-asset-generator** | Favicons, app icons, social media images | Community |

---

## Frameworks & Tools

### Agent Management

| Tool | Description | Link |
|------|-------------|------|
| **webdevtodayjason/sub-agents** | NPM-installable CLI manager with context-forge | [GitHub](https://github.com/webdevtodayjason/sub-agents) |
| **baryhuang/claude-code-by-agents** | Desktop app with @agent mentions | [GitHub](https://github.com/baryhuang/claude-code-by-agents) |
| **Dicklesworthstone/claude_code_agent_farm** | Multiple parallel Claude sessions | [GitHub](https://github.com/Dicklesworthstone/claude_code_agent_farm) |

### Session & History Tools

| Tool | Description | Link |
|------|-------------|------|
| **cc-sessions** | Opinionated productive development approach | Community |
| **cchistory** | Command history viewer for sessions | Community |
| **cclogviewer** | HTML UI for conversation files | Community |
| **Recall** | Full-text search for Claude Code sessions | Community |

### Claude Agent SDK

The official SDK for building production-ready agents:

```bash
# Python
pip install claude-agent-sdk

# TypeScript/Node
npm install @anthropic-ai/claude-agent-sdk
```

**Key Features:**
- Context management with automatic compaction
- Rich tool ecosystem (file ops, code execution, web search, MCP)
- Fine-grained permissions
- Built-in error handling, session management, monitoring

**Resources:**
- [Agent SDK Overview](https://docs.claude.com/en/api/agent-sdk/overview)
- [SDK Demos Repository](https://github.com/anthropics/claude-agent-sdk-demos)
- [Python SDK](https://github.com/anthropics/claude-agent-sdk-python)

---

## Workflow Patterns

### Agentic Workflow Patterns

| Pattern | Description |
|---------|-------------|
| **Subagent Orchestration** | Main agent delegates to specialized subagents |
| **Progressive Skills** | Load skills dynamically as needed |
| **Parallel Tool Calling** | Execute multiple independent tools simultaneously |
| **Master-Clone Architecture** | Primary agent with specialized clones |
| **Wizard Workflows** | Step-by-step guided processes |

### Recommended Agent Combinations

**Essential Starter Set:**
```
code-reviewer + security-auditor + performance-optimizer
```

**Full Development Team:**
```
backend-architect + frontend-developer + qa-expert + security-auditor
```

**Architecture Support:**
```
system-architect + api-designer + data-architect
```

### Workflow Systems

| System | Description | Link |
|--------|-------------|------|
| **RIPER Workflow** | Research, Innovate, Plan, Execute, Review | Community |
| **AB Method** | Spec-driven workflow for large problems | Community |
| **Claude Code PM** | Feature-packed project management | [GitHub](https://github.com/hesreallyhim/awesome-claude-code) |
| **Simone** | Broader project management system | Community |

---

## Creating Your Own Agent

### Step 1: Define the Role

```markdown
---
name: your-agent-name
description: Use this agent when [specific trigger conditions]
tools: Read, Write, Edit, Bash, Glob, Grep
model: sonnet
---
```

### Step 2: Write the System Prompt

```markdown
You are a [role] with expertise in [domain].

## Responsibilities
- [Primary task 1]
- [Primary task 2]

## Approach
1. [Step 1]
2. [Step 2]
3. [Step 3]

## Output Format
Return results as [format specification].
```

### Step 3: Set Tool Permissions

| Agent Type | Recommended Tools |
|------------|-------------------|
| Read-only (reviewers, auditors) | Read, Grep, Glob |
| Research (analysts) | Read, Grep, Glob, WebFetch, WebSearch |
| Writers (developers) | Read, Write, Edit, Bash, Glob, Grep |
| Full access (architects) | All tools |

### Step 4: Test and Iterate

```bash
# Test your agent
"Use my-agent to [specific task]"

# Refine based on results
# Adjust system prompt, tools, or model as needed
```

---

## Best Practices

### Agent Design

1. **Single Responsibility** - Create focused agents with one clear purpose
2. **Minimal Tools** - Only grant necessary tools for security and focus
3. **Clear Triggers** - Write descriptions that make automatic invocation predictable
4. **Concise Prompts** - Keep system prompts focused to control token costs

### Usage Patterns

1. **Start Small** - Begin with the essential starter set before expanding
2. **Combine Strategically** - Use multi-agent workflows for complex tasks
3. **Monitor Context** - Watch for context pollution in long sessions
4. **Batch Efficiently** - Limit to 10 parallel agents maximum

### Maintenance

1. **Version Control** - Keep agents in `.claude/agents/` under git
2. **Document Changes** - Track agent iterations and improvements
3. **Share with Team** - Use project-level agents for consistency
4. **Regular Review** - Update agents as your workflow evolves

---

## Community Resources

### Directories & Aggregators

- [subagents.cc](https://subagents.cc/) - Dedicated Claude agent directory
- [awesomeclaude.ai](https://awesomeclaude.ai/) - Comprehensive Claude resources

### Community Hubs

- [r/ClaudeAI](https://reddit.com/r/ClaudeAI) - Reddit community
- [GitHub Topics: claude-agents](https://github.com/topics/claude-agents) - GitHub discovery
- [GitHub Topics: claude-code](https://github.com/topics/claude-code) - Broader ecosystem

### Learning Resources

- [Building Agents with the Claude Agent SDK](https://www.anthropic.com/engineering/building-agents-with-the-claude-agent-sdk) - Official guide
- [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices) - Anthropic engineering
- [Agent Skills Deep Dive](https://leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/) - First principles analysis

### Curated Lists

- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) - Commands, workflows, CLAUDE.md files
- [awesome-claude](https://github.com/alvinunreal/awesome-claude) - General Claude resources
- [awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) - Skills collection

---

## Contributing

Contributions are welcome! Please read the contribution guidelines before submitting:

1. **Fork** the repository
2. **Add** your agent, tool, or resource to the appropriate section
3. **Follow** the existing format for consistency
4. **Submit** a pull request with a clear description

### Submission Format

For agents:
```markdown
| **agent-name** | Brief description of functionality | [GitHub](link) |
```

For collections:
```markdown
| **author/repo** | Count | Description | [GitHub](link) |
```

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

This list is released under CC0 1.0 Universal. The individual projects listed have their own licenses.

---

## Acknowledgments

Special thanks to:
- [Anthropic](https://www.anthropic.com/) for Claude and the Agent SDK
- The Claude Code community for creating and sharing agents
- All the maintainers of the collections featured here

---

<p align="center">
  <sub>If you find this useful, please star the repo and share with others!</sub>
</p>
