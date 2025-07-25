# Copilot Instructions for Solo-Dev Workflow Testing

This repository implements a comprehensive instruction management system for AI-assisted development, combining multiple workflow methodologies and coding standards.

## Architecture Overview

This is a **multi-layered instruction orchestration system** built around structured AI-assisted development:

- **`.github/instructions/`** - Comprehensive coding standards and workflow definitions with YAML frontmatter for file targeting
- **`.github/prompts/`** - Reusable prompt templates for workflow phases
- **`.github/scripts/`** - Git hooks and automation (`commit-msg` enforces 15+ char messages)  
- **`.github/workflows/`** - CI pipeline expects Python projects with pytest + coverage
- **`docs/`** - Living documentation updated after each feature

## Instruction System Architecture

### File-Pattern-Based Instructions
The `.github/instructions/` directory contains specialized instruction files with YAML frontmatter defining their scope:

- **`flow.instructions.md`** - Core Solo-Dev Copilot 5-phase TDD workflow (`applyTo: '**'`)
- **`python.instructions.md`** - Python coding conventions, PEP 8, type hints (`applyTo: '**/*.py'`)
- **`github-actions-ci-cd-best-practices.instructions.md`** - Comprehensive CI/CD patterns (`applyTo: '.github/workflows/*.yml'`)
- **`vuejs3.instructions.md`** - Vue.js 3 with Composition API standards (`applyTo: '**/*.vue, **/*.ts, **/*.js, **/*.scss'`)
- **`spec-driven-workflow-v1.instructions.md`** - Requirements → Design → Tasks methodology (`applyTo: '**'`)
- **`markdown.instructions.md`** - Documentation standards (`applyTo: '**/*.md'`)

### Workflow Methodologies

#### Solo-Dev Copilot (Primary)
1. **Analyse Codebase** → Generate `docs/current-state.md` with Mermaid diagrams
2. **Strategy** → Create roadmap with 1-3 milestones, await "Strategy Confirmed"
3. **Task Breakdown** → Split into ≤4h tasks with acceptance criteria
4. **Implementation** → Red-Green-Refactor cycle, wait for "Approve" or "Modify"
5. **Deliverables** → Update docs + generate `docs/summary.md`

#### Spec-Driven Workflow (Secondary)
- Maintain `requirements.md`, `design.md`, `tasks.md` as source of truth
- EARS notation for user stories
- Technical architecture with sequence diagrams

### Key Conventions
- **Language Mix**: Italian headings for structure, technical English for clarity
- **Test-First**: Every feature starts with failing tests (pytest expected)
- **Coverage Target**: ≥80% coverage via `pytest --cov=src --cov-report=xml`
- **Instruction Scope**: Use YAML frontmatter `applyTo` patterns to target specific file types

## Project-Specific Patterns

### Instruction File Structure
All instruction files follow this pattern:
```yaml
---
description: 'Brief description of the instruction set'
applyTo: 'glob pattern for file targeting'
---
```

### Prompt Templates
Use structured prompts from `.github/prompts/`:
- `analysis.md` - For current-state reports with PATH-LIST placeholder
- `strategy.md` - Roadmap generation with milestone tables
- `task.md` - Task breakdown with Gherkin acceptance criteria

### Multi-Technology Support
- **Python**: PEP 8, type hints, docstrings, pytest patterns
- **JavaScript/Vue.js**: Composition API, TypeScript, SCSS standards
- **CI/CD**: GitHub Actions best practices, security, caching strategies
- **Documentation**: Markdown standards, Mermaid diagrams

## Working with This Codebase

When implementing new features:
1. Reference `flow.instructions.md` for the complete Solo-Dev methodology
2. Apply technology-specific instructions based on file patterns
3. Use prompt templates to maintain consistency
4. Follow TDD: tests first, then implementation
5. Update `docs/` folder after feature completion
6. Ensure Italian structural headings with English technical content

The system is designed for **solo developers** who want comprehensive AI assistance while maintaining control over technical decisions across multiple technology stacks.
