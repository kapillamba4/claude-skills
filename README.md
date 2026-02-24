# Claude Skills

A collection of reusable skills for Claude Code that enhance productivity and standardize workflows.

## What are Claude Skills?

Claude Skills follow the [Agent Skills specification](https://agentskills.io) - structured workflows and behaviors for AI agents. Each skill is a directory containing a `SKILL.md` file with YAML frontmatter.

## Available Skills

### [architect](./architect/)

Transform vague requirements into implementation-ready prompts through iterative clarification and meta-prompting.

**Triggers:**
- `/architect`
- Auto-detects vague requests (with confirmation)

**Workflow:**
1. Ask clarifying questions (2-3 rounds)
2. Fetch Anthropic and Google prompting guides
3. Generate a ready-to-use meta-prompt
4. User reviews and approves
5. Implementation begins

### [ux-lens](./ux-lens/)

Perform a comprehensive UX & UI audit of any website via browser. Analyzes accessibility, visual design, usability, and user experience patterns.

**Triggers:**
- `/ux-lens [URL]`
- Auto-detects requests to review, audit, or evaluate website design

**Audit Categories:**
- Accessibility (WCAG 2.1 compliance)
- Visual Design (hierarchy, typography, color)
- Usability (navigation, CTAs, forms)
- UX Patterns (onboarding, empty states, micro-interactions)
- Mobile Responsiveness

**Output:**
- Severity-classified findings (Critical/Major/Minor/Suggestion)
- Score overview by category
- Prioritized action items

## Installation

### Option 1: Git Submodule (Recommended)

Add this repo as a submodule to your project:

```bash
git submodule add https://github.com/kapillamba4/claude-skills.git .claude/skills
```

### Option 2: Clone into Project

```bash
git clone https://github.com/kapillamba4/claude-skills.git .claude/skills
```

### Option 3: Copy Individual Skills

Copy specific skill directories to your project's `.claude/skills/` directory:

```bash
# Create the skills directory
mkdir -p .claude/skills

# Copy a skill
cp -r architect .claude/skills/
```

### Option 4: Global Installation (User-level)

Clone to your user-level Claude directory to make skills available across all projects:

```bash
# Create directory if it doesn't exist
mkdir -p ~/.claude/skills

# Clone skills globally
git clone https://github.com/kapillamba4/claude-skills.git ~/.claude/skills
```

Or add as a submodule if you track your dotfiles with git:

```bash
git submodule add https://github.com/kapillamba4/claude-skills.git ~/.claude/skills
```

### Option 5: Symlink Individual Skills

Clone to a central location and create symlinks in specific projects:

```bash
# Clone to a central location
git clone https://github.com/kapillamba4/claude-skills.git ~/claude-skills

# Link to a project
ln -s ~/claude-skills/architect /path/to/project/.claude/skills/
```

## Usage

Once installed, invoke skills using slash commands:

```
/architect I want to build a task tracker
```

## Skill Structure

Each skill follows the Agent Skills specification:

```
skill-name/
└── SKILL.md          # Required: YAML frontmatter + Markdown instructions
```

## Adding New Skills

Create a new skill directory with a `SKILL.md` file:

```bash
mkdir -p my-skill
```

```markdown
---
name: my-skill
description: Brief description of what this skill does and when to use it.
---

# My Skill

Detailed instructions for the skill...

## Workflow
1. Step one
2. Step two
```

## License

[MIT](./LICENSE)
