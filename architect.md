# Architect

Transform vague requirements into implementation-ready prompts through iterative clarification and meta-prompting.

## Triggers

- **Slash command**: `/architect`
- **Auto-detect**: When a request is clearly vague or ambiguous, ask the user if they want to use this workflow before proceeding

## Workflow

### Step 1: Clarification Loop

Ask 2-4 focused questions at a time using `AskUserQuestion`. Target these areas:

| Category | Example Questions |
|----------|-------------------|
| **Scope** | What exactly needs to be built? What's out of scope? |
| **Context** | Who will use this? What's the use case? |
| **Constraints** | Tech stack? Platform? Performance needs? |
| **Success** | How will you know it's working correctly? |

Continue for 2-3 rounds until you have sufficient clarity.

### Step 2: Fetch Prompting Guides

Call both MCP tools in parallel:
- `mcp__meta-prompt-mcp__get_anthropic_guide`
- `mcp__meta-prompt-mcp__get_google_guide`

Synthesize relevant techniques from both guides.

### Step 3: Generate Meta-Prompt

Create a single, ready-to-use prompt that incorporates:
- Clear role/context setting
- Specific requirements extracted from clarifications
- Appropriate constraints
- Defined output format
- Success criteria

### Step 4: User Review

Present the raw prompt in a code block and ask:

> **Review this prompt. Would you like to:**
> - **Approve** - Proceed with implementation
> - **Revise** - Tell me what to change
> - **Regenerate** - Try a different approach

Iterate until approved.

### Step 5: Implement

Execute the approved prompt and build the solution.

## Output Template

After clarification, present the meta-prompt like this:

```
## Meta-Prompt

```[programming language]
[The complete, ready-to-use prompt text]
```

**Review:** Approve / Revise / Regenerate?
```

## Example

**User**: I want to build a task tracker

**Round 1 Questions**:
- Personal or team use?
- Platform preference (CLI, web, desktop)?
- Essential features?

**Round 2 Questions** (if needed):
- Data persistence method?
- Any integrations needed?

**Generated Meta-Prompt**:
```
You are building a personal CLI task tracker in Python...

Requirements:
- Add, list, complete, delete tasks
- Store tasks in ~/.tasks.json
- Support priority levels (high/medium/low)
- Due date support with natural language parsing

Output:
- Single Python file: tracker.py
- Include --help documentation
- Handle edge cases gracefully

Success criteria:
- All CRUD operations work
- Data persists between sessions
- Clear error messages
```

**Review**: Approve to begin implementation.
```
