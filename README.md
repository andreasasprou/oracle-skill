# Oracle Skill for Claude Code

A Claude Code plugin that gives Claude access to an "Oracle" - GPT-5.2 with deep reasoning capabilities for strategic technical advice.

## What is Oracle?

Oracle is a read-only technical advisor powered by GPT-5.2 with maximum reasoning depth (`xhigh`). It can:

- **Read files** and explore your codebase
- **Run shell commands** for investigation
- **Search the web** for current information
- **Provide strategic advice** with structured responses

It **cannot** edit files or make changes - it's purely advisory, making it safe to consult without risk of unintended modifications.

## Installation

### Prerequisites

1. **Codex CLI** installed and authenticated:
   ```bash
   npm install -g @openai/codex
   codex login
   ```

2. **Access to GPT-5.2** model in your OpenAI account

### Install the Plugin

```bash
# Add the marketplace
/plugin marketplace add andreasasprou/oracle-skill

# Install the plugin
/plugin install oracle@oracle-marketplace

# Restart Claude Code to load the skill
```

## Usage

The oracle skill is automatically invoked when you ask Claude for:
- Architecture decisions
- Complex debugging help
- Security analysis
- Trade-off analysis
- Code review opinions

Or explicitly ask: "Ask the oracle about..."

### Example Questions

- "Ask the oracle: Given our PostgreSQL + Redis stack, should we add Elasticsearch for full-text search or use pg_trgm? We have 10M records, 100 QPS expected."
- "Oracle, analyze the security implications of this authentication flow"
- "What does the oracle think about migrating from our custom event system to a standard library?"

### Background Execution

For complex questions requiring deep reasoning, Claude will automatically run the oracle in the background and poll for results, allowing you to continue working.

## Response Format

Oracle responses follow a tiered structure:

### Essential (Always Present)
- **Bottom Line**: 1-2 sentence direct answer
- **Action Plan**: Numbered concrete next steps
- **Effort Estimate**: Quick (<1h) | Short (1-4h) | Medium (1-2d) | Large (3d+)

### Expanded (When Relevant)
- **Reasoning**: Why this approach over alternatives
- **Trade-offs**: What you gain vs sacrifice
- **Dependencies**: Prerequisites and external factors

### Edge Cases (When Applicable)
- **Escalation Triggers**: When to reconsider
- **Alternatives**: Backup options
- **Gotchas**: Common mistakes to avoid

## Configuration

The oracle uses these Codex CLI settings:
- **Model**: `gpt-5.2`
- **Reasoning effort**: `xhigh` (maximum depth)
- **Sandbox**: `read-only` (cannot write files)
- **File editing**: Disabled
- **Web search**: Enabled

## License

MIT
