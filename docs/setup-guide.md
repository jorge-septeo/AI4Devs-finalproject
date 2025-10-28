# RepoAgents Setup Guide

## 📋 Table of Contents
1. [Quick Start](#quick-start)
2. [Installing Agent Tools](#installing-agent-tools)
3. [Configuring Your Repository](#configuring-your-repository)
4. [Using Each Agent](#using-each-agent)
5. [Troubleshooting](#troubleshooting)

---

## Quick Start

### Prerequisites
- Git installed
- GitHub account with access to the repository
- Node.js 18+ (for running examples)
- Access to at least one AI agent platform

### 1. Clone or Adapt the Structure

This is an educational project. You can adapt the structure for your own use:

```bash
# If you have access to the repository
git clone https://github.com/jorge-septeo/AI4Devs-finalproject.git my-project
cd my-project

# Or recreate the structure in your own project
```

### 2. Customize AGENTS.md

Edit the main `AGENTS.md` file with your project specifics:

```bash
# Open in your editor
code AGENTS.md
```

Key sections to update:
- Project Overview
- Setup Commands
- Project Structure
- Development Guidelines

### 3. Choose Your Agents

Pick which agents you want to use and remove others:

```bash
# Example: Keep only Copilot and Claude
rm -rf agents/gemini agents/opencode agents/jules
```

Or keep all and configure them individually!

---

## Installing Agent Tools

### GitHub Copilot

**Requirements**: GitHub Copilot subscription

**Setup**:
1. Install [VS Code](https://code.visualstudio.com/)
2. Install GitHub Copilot extension
3. Sign in with your GitHub account
4. The `.github/copilot-instructions.md` will be automatically detected

**Verification**:
```bash
# Open any code file in VS Code
# Type a comment describing what you want
# Copilot should suggest code
```

### Google Gemini CLI

**Requirements**: Google AI account

**Installation**:
```bash
npm install -g @google/generative-ai-cli
```

**Setup**:
```bash
# Set your API key
export GEMINI_API_KEY="your-api-key-here"

# Or add to your shell profile (~/.zshrc or ~/.bashrc)
echo 'export GEMINI_API_KEY="your-api-key-here"' >> ~/.zshrc
```

**Configuration**:
The `agents/gemini/.gemini/settings.json` file is already configured!

**Usage**:
```bash
# Navigate to project root
cd my-project

# Ask Gemini to help
gemini "Review the authentication module"
```

### Anthropic Claude

**Requirements**: Claude API access

**Setup**:
```bash
# Install Claude CLI (if available) or use Claude.ai
# For API usage:
export CLAUDE_API_KEY="your-api-key-here"
```

**Usage**:
- Use Claude.ai and upload project files
- Reference `agents/claude/claude-config.md` in your prompts
- Or integrate via API in your workflows

### OpenAI Codex

**Requirements**: OpenAI API access

**Setup**:
```bash
# Install OpenAI CLI
npm install -g openai

# Set API key
export OPENAI_API_KEY="your-api-key-here"
```

**Usage**:
```bash
# Use with your preferred OpenAI interface
# Follow instructions in AGENTS.md
```

### OpenCode

**Requirements**: OpenCode compatible editor

**Installation**:
Follow [OpenCode documentation](https://opencode.ai/docs)

**Configuration**:
The `agents/opencode/opencode-rules.md` file contains all rules!

### Google Jules

**Requirements**: Jules access (currently limited beta)

**Setup**:
Request access at [jules.google](https://jules.google/)

**Configuration**:
Follow `agents/jules/jules-config.md` once you have access.

---

## Configuring Your Repository

### 1. Set Up GitHub Actions

The workflows are ready to use! Enable them:

1. Go to your repository on GitHub
2. Click "Actions" tab
3. Enable workflows
4. Push a commit to trigger them

**Available Workflows**:
- `agent-code-review.yml` - Automatic PR reviews
- `agent-testing.yml` - Test validation

### 2. Configure Branch Protection

Recommended settings for `main` branch:

1. Go to Settings → Branches
2. Add rule for `main`
3. Enable:
   - ✅ Require pull request reviews
   - ✅ Require status checks (select the agent workflows)
   - ✅ Require branches to be up to date

### 3. Set Up Issue Templates

Templates are already in `.github/ISSUE_TEMPLATE/`!

Test them:
1. Go to Issues → New Issue
2. You'll see "Feature Request" template
3. Fill it out - agents can process these!

### 4. Add Repository Secrets

For workflows that need API access:

1. Go to Settings → Secrets and variables → Actions
2. Add secrets:
   - `GEMINI_API_KEY`
   - `CLAUDE_API_KEY`
   - `OPENAI_API_KEY`
   - etc.

---

## Using Each Agent

### GitHub Copilot Workflow

**Best for**: Real-time code completion, inline suggestions

**Daily usage**:
1. Open project in VS Code
2. Start coding - Copilot suggests as you type
3. Use Copilot Chat for questions
4. Reference project context automatically via `.github/copilot-instructions.md`

**Tips**:
- Write descriptive comments to get better suggestions
- Use `Ctrl+Enter` to see alternative suggestions
- Ask in Chat: "Explain this code" or "Add tests for this function"

### Gemini CLI Workflow

**Best for**: Code review, documentation, complex analysis

**Example commands**:
```bash
# Review code quality
gemini "Review the authentication module for security issues"

# Generate documentation
gemini "Create API documentation for src/api/users.ts"

# Explain complex code
gemini "Explain how the caching mechanism works in src/cache/"

# Suggest improvements
gemini "Suggest performance improvements for the database queries"
```

**In PRs**:
```bash
# Review a specific PR
gemini "Review PR #123 for code quality and potential bugs"
```

### Claude Workflow

**Best for**: Architecture reviews, refactoring, in-depth analysis

**Via Claude.ai**:
1. Start new conversation
2. Upload relevant files or paste code
3. Reference: "Follow the guidelines in claude-config.md"
4. Ask for review, refactoring, or implementation

**Example prompts**:
```
I'm working on the RepoAgents project. Here's the authentication module.
Following the claude-config.md guidelines, please:
1. Review for security issues
2. Suggest architectural improvements
3. Identify any code smells

[paste code or attach files]
```

### Issue-Based Agent Interaction

**Create issues for agents to work on**:

```markdown
---
title: "[Feature] Add user authentication"
labels: ["enhancement", "agent-task"]
assignees: []
---

## Task
Implement JWT-based authentication for the API

## Acceptance Criteria
- [ ] JWT token generation on login
- [ ] Token validation middleware
- [ ] Refresh token mechanism
- [ ] Tests with >90% coverage

## Technical Notes
- Use jsonwebtoken library
- Store refresh tokens in Redis
- Follow security best practices from AGENTS.md

## Files to Create/Modify
- `src/auth/jwt.ts`
- `src/middleware/auth.ts`
- `tests/auth.test.ts`

@claude @jules Please implement this following the project guidelines.
```

---

## Troubleshooting

### Copilot not seeing instructions

**Solution**:
- Ensure `.github/copilot-instructions.md` exists
- Reload VS Code window
- Check Copilot is enabled for the workspace

### Gemini not using AGENTS.md

**Solution**:
- Verify `agents/gemini/.gemini/settings.json` has `"contextFileName": "AGENTS.md"`
- Make sure you're in the project root directory
- Update Gemini CLI: `npm update -g @google/generative-ai-cli`

### Workflows not running

**Solution**:
- Check Actions are enabled in repository settings
- Verify workflow files have no syntax errors
- Check branch protection rules aren't blocking

### Agent suggestions don't match project style

**Solution**:
- Update AGENTS.md with more specific examples
- Add your actual code patterns to agent configs
- Include more context in prompts

### API rate limits

**Solution**:
- Implement caching in workflows
- Use conditional workflow triggers
- Batch requests when possible

### Secrets not working in workflows

**Solution**:
- Verify secret names match exactly (case-sensitive)
- Check secrets are set in correct scope (repository vs. environment)
- Use `${{ secrets.SECRET_NAME }}` syntax in workflows

---

## Next Steps

1. ✅ **Customize configurations** for your project
2. ✅ **Try each agent** to see which works best for you
3. ✅ **Create your first AI-assisted PR**
4. ✅ **Iterate and improve** your AGENTS.md based on results

## Additional Resources

- [AGENTS.md Specification](https://agents.md/)
- [Agent Comparison Matrix](./agent-comparison.md)
- [Example Project](../examples/)
- [GitHub Copilot Docs](https://docs.github.com/en/copilot)
- [Gemini API Docs](https://ai.google.dev/docs)

---

**Questions?** Create an issue and let an agent help you! 🤖
