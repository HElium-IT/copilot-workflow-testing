# Copilot Instructions for Solo-Dev Workflow Testing

This repository implements a structured TDD workflow for personal projects using the "Solo-Dev Copilot" methodology.

## Architecture Overview

This is a **workflow orchestration system** built around structured AI-assisted development:

- **`.github/instructions/`** - Core flow definitions (`flow.instruction.md` defines the 5-phase workflow)
- **`.github/prompts/`** - Reusable prompt templates for each workflow phase
- **`.github/scripts/`** - Git hooks and automation (`commit-msg` enforces 15+ char messages)  
- **`.github/workflows/`** - CI pipeline expects Python projects with pytest + coverage
- **`docs/`** - Living documentation updated after each feature

## Development Workflow (TDD-First)

### The 5-Phase Flow
1. **Analyse Codebase** → Generate `docs/current-state.md` with Mermaid diagrams
2. **Strategy** → Create roadmap with 1-3 milestones, await "Strategy Confirmed"
3. **Task Breakdown** → Split into ≤4h tasks with acceptance criteria
4. **Implementation** → Red-Green-Refactor cycle, wait for "Approve" or "Modify"
5. **Deliverables** → Update docs + generate `docs/summary.md`

### Key Conventions
- **Language Mix**: Italian headings for structure, technical English for clarity
- **Test-First**: Every feature starts with failing tests (pytest expected)
- **Coverage Target**: ≥80% coverage via `pytest --cov=src --cov-report=xml`
- **Branching**: main + feature branches with PR-based workflow

## Project-Specific Patterns

### Prompt Templates
Use structured prompts from `.github/prompts/`:
- `analysis.md` - For current-state reports with PATH-LIST placeholder
- `strategy.md` - Roadmap generation with milestone tables
- `task.md` - Task breakdown with Gherkin acceptance criteria

### Documentation Standards
- Generate Mermaid diagrams for architecture visualization
- Maintain `docs/current-state.md` for technical debt tracking
- Create `docs/summary.md` for non-technical stakeholders
- Use Italian section headers: "Analizza", "Strategia", etc.

### CI/CD Integration
- Python 3.12 runtime assumption
- Expects `requirements.txt` in project root
- Coverage artifacts uploaded for tracking
- Commit message validation (15+ characters)

## Working with This Codebase

When implementing new features:
1. Reference `flow.instruction.md` for the complete methodology
2. Use prompt templates to maintain consistency
3. Follow TDD: tests first, then implementation
4. Update `docs/` folder after feature completion
5. Ensure Italian structural headings with English technical content

The workflow is designed for **solo developers** who want structured AI assistance while maintaining control over technical decisions.
