# aw-conductor

GitHub Agentic Workflow implementation of the [Gemini CLI Conductor](https://github.com/gemini-cli-extensions/conductor) extension.

## Overview

Conductor enables **Context-Driven Development** by enforcing a strict protocol: **Context → Spec & Plan → Implement**.

This repository contains a GitHub Agentic Workflow that brings Conductor's functionality to GitHub Issues, allowing you to:
- Initialize project context (product, tech stack, workflow, guidelines)
- Create feature/bug tracks with detailed specs and plans
- Implement tasks following your defined workflow
- Review and track progress
- Revert work when needed

## Usage

### Setup

Label an issue with `conductor` and use one of the following commands in the issue description or comments:

### Available Commands

#### `/conductor:setup`
Initialize the Conductor framework for your project (run once per project).

Creates the conductor directory structure with:
- `conductor/product.md` - Product definition and goals
- `conductor/tech-stack.md` - Technical stack and preferences
- `conductor/workflow.md` - Development workflow and practices
- `conductor/product-guidelines.md` - Standards and guidelines
- `conductor/tracks.md` - Registry of all tracks

#### `/conductor:newTrack`
Start a new feature or bug track.

Example:
```
/conductor:newTrack "Add dark mode toggle to settings page"
```

This will:
1. Generate a unique track ID
2. Create detailed specification (`spec.md`)
3. Generate implementation plan (`plan.md`) with phases and tasks
4. Create a PR with the new track

#### `/conductor:implement`
Execute tasks from the current track's implementation plan.

The workflow will:
1. Find the next uncompleted task
2. Follow your defined workflow (e.g., TDD: test → fail → implement → pass)
3. Update the plan as tasks complete
4. Create commits with descriptive messages
5. Request verification at phase boundaries

#### `/conductor:status`
Display current project progress showing all tracks and their status.

#### `/conductor:review`
Review completed work against guidelines and the implementation plan.

#### `/conductor:revert`
Revert a track, phase, or task by analyzing git history.

## File Structure

```
conductor/
├── index.md                          # Links to all context files
├── product.md                        # Product definition and goals
├── product-guidelines.md             # Standards and guidelines
├── tech-stack.md                     # Technical preferences
├── workflow.md                       # Development workflow
├── tracks.md                         # Registry of all tracks
├── code_styleguides/                 # Language-specific style guides
└── tracks/                           # Individual track folders
    └── <track_id>/
        ├── index.md                  # Links to track artifacts
        ├── spec.md                   # Detailed specification
        ├── plan.md                   # Implementation plan
        └── metadata.json             # Track metadata
```

## How It Works

1. **Label an issue** with `conductor`
2. **Use a command** in the issue (e.g., `/conductor:newTrack "Feature description"`)
3. **The workflow runs** and executes the appropriate Conductor command
4. **Artifacts are created** in the `conductor/` directory
5. **PRs are generated** for review and merging
6. **Progress is tracked** in issue comments

## Benefits

- **Structured Development**: Enforce consistent planning and implementation
- **Persistent Context**: All project context is versioned with your code
- **Team Collaboration**: Shared context files ensure everyone follows the same guidelines
- **AI-Friendly**: Rich context helps AI assistants make better decisions
- **Audit Trail**: Complete history of specs, plans, and implementations

## Related

- [Gemini CLI Conductor Extension](https://github.com/gemini-cli-extensions/conductor)
- [GitHub Agentic Workflows](https://github.github.com/gh-aw/)