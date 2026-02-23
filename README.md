# Claude Skills

A collection of reusable skills for Claude Code that enhance productivity and standardize workflows.

## What are Claude Skills?

Claude Skills are markdown files that define structured workflows and behaviors for Claude Code. They can be invoked via slash commands or triggered automatically based on context.

## Available Skills

### [Clarify and Implement](./clarify-and-implement.md)

Transform vague requirements into implementation-ready prompts through iterative clarification and meta-prompting.

**Triggers:**
- `/clarify` or `/clarify-and-implement`
- Auto-detects vague requests (with confirmation)

**Workflow:**
1. Ask clarifying questions (2-3 rounds)
2. Fetch Anthropic and Google prompting guides
3. Generate a ready-to-use meta-prompt
4. User reviews and approves
5. Implementation begins

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

Copy specific skill files to your project's `.claude/` directory:

```bash
curl -o .claude/clarify-and-implement.md https://raw.githubusercontent.com/kapillamba4/claude-skills/main/clarify-and-implement.md
```

### Option 4: Global Installation (User-level)

Clone to your user-level Claude directory to make skills available across all projects:

```bash
# Create directory if it doesn't exist
mkdir -p ~/.claude

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
ln -s ~/claude-skills/clarify-and-implement.md /path/to/project/.claude/
```

## Usage

Once installed, invoke skills using slash commands:

```
/clarify I want to build a task tracker
```

## Adding New Skills

Create a new markdown file with:

```markdown
# Skill Name

Brief description of what the skill does.

## Triggers
- `/command-name`
- Auto-detect conditions

## Workflow
1. Step one
2. Step two
...
```

## License

[MIT](./LICENSE)
