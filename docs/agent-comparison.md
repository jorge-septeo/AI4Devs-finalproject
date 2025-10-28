# Agent Comparison Matrix

A comprehensive comparison of AI coding agents supported by RepoAgents.

## Quick Reference Table

| Feature | GitHub Copilot | Gemini CLI | Claude | Codex | OpenCode | Jules | Factory |
|---------|---------------|------------|---------|-------|----------|-------|---------|
| **Real-time suggestions** | ✅ Excellent | ⚠️ Limited | ❌ No | ⚠️ API only | ✅ Good | ⚠️ Limited | ⚠️ Limited |
| **Code review** | ⚠️ Basic | ✅ Excellent | ✅ Excellent | ✅ Good | ✅ Excellent | ✅ Excellent | ✅ Good |
| **Test generation** | ✅ Good | ✅ Excellent | ✅ Excellent | ✅ Good | ✅ Good | ✅ Excellent | ✅ Good |
| **Documentation** | ⚠️ Basic | ✅ Excellent | ✅ Excellent | ✅ Good | ✅ Good | ✅ Good | ⚠️ Basic |
| **Refactoring** | ⚠️ Basic | ✅ Good | ✅ Excellent | ✅ Good | ✅ Good | ✅ Excellent | ✅ Good |
| **Multi-file changes** | ⚠️ Limited | ✅ Good | ✅ Good | ✅ Good | ✅ Good | ✅ Excellent | ✅ Excellent |
| **Architecture suggestions** | ❌ No | ✅ Good | ✅ Excellent | ⚠️ Limited | ✅ Good | ✅ Good | ✅ Good |
| **GitHub integration** | ✅ Native | ⚠️ Manual | ⚠️ Manual | ⚠️ API | ⚠️ Manual | ⚠️ API | ⚠️ API |
| **Offline capability** | ❌ No | ❌ No | ❌ No | ❌ No | ⚠️ Partial | ❌ No | ❌ No |
| **AGENTS.md support** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |

**Legend**:
- ✅ Excellent/Full support
- ⚠️ Partial/Limited support
- ❌ Not supported

---

## Detailed Comparison

### 1. GitHub Copilot

**Best for**: Real-time code completion and quick suggestions

**Strengths**:
- ✅ Seamless IDE integration (VS Code, JetBrains, Neovim)
- ✅ Real-time inline suggestions
- ✅ Context-aware completions
- ✅ Native GitHub integration
- ✅ Chat interface for questions
- ✅ Fast response times

**Weaknesses**:
- ❌ Limited architectural reasoning
- ❌ Can't handle complex multi-file refactoring
- ⚠️ Basic code review capabilities
- ⚠️ Suggestions can be repetitive

**Pricing**: $10/month (individual), $19/month (business)

**Setup difficulty**: ⭐ Easy

**Configuration file**: `.github/copilot-instructions.md`

**Use cases**:
- Autocompleting functions and classes
- Writing tests for individual functions
- Quick refactoring of small code blocks
- Learning new APIs or libraries
- Boilerplate code generation

---

### 2. Google Gemini CLI

**Best for**: Code analysis and documentation generation

**Strengths**:
- ✅ Excellent natural language understanding
- ✅ Great at documentation generation
- ✅ Strong code review capabilities
- ✅ CLI integration for automation
- ✅ Large context window
- ✅ Multi-modal (can analyze images/diagrams)

**Weaknesses**:
- ⚠️ Not real-time in editors
- ⚠️ Manual workflow integration
- ⚠️ Rate limits on free tier

**Pricing**: Free tier available, paid plans from $0.001/1K characters

**Setup difficulty**: ⭐⭐ Moderate

**Configuration file**: `agents/gemini/.gemini/settings.json`

**Use cases**:
- Comprehensive code reviews
- API documentation generation
- Explaining complex code sections
- Suggesting architectural improvements
- Analyzing security vulnerabilities

---

### 3. Anthropic Claude

**Best for**: In-depth code review and architectural analysis

**Strengths**:
- ✅ Exceptional reasoning capabilities
- ✅ Excellent at explaining complex code
- ✅ Strong refactoring suggestions
- ✅ Great architectural insights
- ✅ Very good at following guidelines
- ✅ Large context window (200K tokens)

**Weaknesses**:
- ⚠️ No native IDE integration
- ⚠️ Requires copy-paste workflow or API integration
- ⚠️ Can be verbose

**Pricing**: API access from $0.25/1M input tokens

**Setup difficulty**: ⭐⭐ Moderate

**Configuration file**: `agents/claude/claude-config.md`

**Use cases**:
- Architectural reviews and suggestions
- Complex refactoring planning
- Security audit and analysis
- Design pattern recommendations
- Code quality improvement strategies

---

### 4. OpenAI Codex

**Best for**: General-purpose code generation and completion

**Strengths**:
- ✅ Strong code generation
- ✅ Good multi-language support
- ✅ API for custom integrations
- ✅ Consistent quality

**Weaknesses**:
- ⚠️ Requires API integration
- ⚠️ No direct IDE integration (use via Copilot)
- ⚠️ Rate limits

**Pricing**: Part of OpenAI API pricing

**Setup difficulty**: ⭐⭐⭐ Advanced (API integration)

**Configuration file**: Referenced in `AGENTS.md`

**Use cases**:
- Custom code generation workflows
- API-based automation
- Code translation between languages
- Algorithm implementation

---

### 5. OpenCode

**Best for**: Enforcing code quality and standards

**Strengths**:
- ✅ Excellent rule enforcement
- ✅ Consistent code style checking
- ✅ Good integration with development workflow
- ✅ Can work offline (for some features)
- ✅ Highly configurable

**Weaknesses**:
- ⚠️ Less creative than other agents
- ⚠️ Focused on rules vs. understanding
- ⚠️ Limited availability

**Pricing**: Varies by implementation

**Setup difficulty**: ⭐⭐ Moderate

**Configuration file**: `agents/opencode/opencode-rules.md`

**Use cases**:
- Enforcing code style guidelines
- Ensuring best practices
- Standardizing code across team
- Pre-commit quality checks

---

### 6. Google Jules

**Best for**: Full-stack feature implementation

**Strengths**:
- ✅ Excellent at multi-file changes
- ✅ Can handle complex features end-to-end
- ✅ Good integration testing
- ✅ Strong workflow automation
- ✅ Understands full project context

**Weaknesses**:
- ⚠️ Currently limited beta access
- ⚠️ Requires specific workflow setup
- ⚠️ Learning curve for optimal use

**Pricing**: TBD (currently in beta)

**Setup difficulty**: ⭐⭐⭐ Advanced

**Configuration file**: `agents/jules/jules-config.md`

**Use cases**:
- Implementing complete features
- Multi-component refactoring
- End-to-end test creation
- Workflow automation
- Large-scale code migrations

---

### 7. Factory AI

**Best for**: Enterprise-grade automation

**Strengths**:
- ✅ Excellent for complex workflows
- ✅ Strong enterprise features
- ✅ Good team collaboration support
- ✅ Advanced automation capabilities

**Weaknesses**:
- ⚠️ Enterprise focused (may be overkill for small projects)
- ⚠️ Higher cost
- ⚠️ Steeper learning curve

**Pricing**: Enterprise pricing (contact sales)

**Setup difficulty**: ⭐⭐⭐⭐ Advanced

**Configuration file**: Referenced in `AGENTS.md`

**Use cases**:
- Enterprise development workflows
- Large team coordination
- Complex CI/CD integration
- Advanced automation pipelines

---

## Recommendation Matrix

### Choose based on your primary need:

| Your Need | Recommended Agent(s) | Alternative |
|-----------|---------------------|-------------|
| **Real-time coding assistance** | GitHub Copilot | - |
| **Code review** | Claude, Gemini CLI | OpenCode |
| **Documentation** | Gemini CLI, Claude | Copilot |
| **Architecture planning** | Claude | Gemini CLI, Jules |
| **Full feature implementation** | Jules | Claude + Copilot |
| **Test generation** | Gemini CLI, Jules | Copilot, Claude |
| **Refactoring** | Claude, Jules | Gemini CLI |
| **Code quality enforcement** | OpenCode | Gemini CLI |
| **Multi-file changes** | Jules, Factory | Claude |
| **Learning and exploration** | Copilot, Gemini CLI | Claude |

### Choose based on your project type:

| Project Type | Recommended Agents |
|-------------|-------------------|
| **Solo hobby project** | Copilot + Gemini CLI (free tier) |
| **Professional solo dev** | Copilot + Claude |
| **Small team (2-5)** | Copilot + Gemini CLI + OpenCode |
| **Medium team (5-20)** | All agents except Factory |
| **Enterprise** | All agents including Factory |
| **Open source** | Copilot + Gemini CLI + Claude |

### Choose based on your budget:

| Budget | Recommended Setup |
|--------|------------------|
| **Free** | Gemini CLI (free tier) |
| **$10-20/month** | GitHub Copilot |
| **$50-100/month** | Copilot + Claude API |
| **$100+/month** | All agents with API access |

---

## Combination Strategies

### 🎯 The Productivity Stack
**Best for**: Maximum day-to-day productivity
- **Primary**: GitHub Copilot (real-time assistance)
- **Secondary**: Gemini CLI (reviews and docs)
- **Tertiary**: Claude (deep analysis as needed)

### 🏗️ The Architecture Stack
**Best for**: Building robust, well-designed systems
- **Primary**: Claude (architectural decisions)
- **Secondary**: Jules (implementation)
- **Tertiary**: Copilot (quick coding)

### 📚 The Documentation Stack
**Best for**: Well-documented projects
- **Primary**: Gemini CLI (doc generation)
- **Secondary**: Claude (complex explanations)
- **Tertiary**: Copilot (inline comments)

### 🧪 The Quality Stack
**Best for**: High-quality, well-tested code
- **Primary**: OpenCode (standards enforcement)
- **Secondary**: Gemini CLI (test generation)
- **Tertiary**: Claude (test strategy)

### 🚀 The Speed Stack
**Best for**: Rapid development
- **Primary**: Jules (full features)
- **Secondary**: Copilot (quick completions)
- **Tertiary**: Gemini CLI (quick reviews)

---

## Integration Workflows

### Workflow 1: Issue to Implementation
```
1. Create issue (GitHub)
2. @jules analyze and plan
3. Jules implements feature
4. GitHub Actions trigger code review
5. Gemini CLI reviews code
6. Claude provides architectural feedback
7. Copilot assists with adjustments
8. OpenCode validates standards
9. Merge!
```

### Workflow 2: PR Review Process
```
1. Create PR (GitHub)
2. GitHub Actions run tests
3. Gemini CLI automated review
4. @claude for manual deep review
5. Developer uses Copilot to address feedback
6. OpenCode final validation
7. Merge!
```

### Workflow 3: Refactoring Workflow
```
1. Claude analyzes codebase
2. Claude suggests refactoring plan
3. Jules implements multi-file changes
4. Gemini CLI generates updated docs
5. Copilot helps with edge cases
6. OpenCode validates consistency
7. Done!
```

---

## Performance Metrics

Based on typical usage patterns:

| Metric | Copilot | Gemini CLI | Claude | Jules | OpenCode |
|--------|---------|------------|--------|-------|----------|
| **Response time** | <1s | 2-5s | 3-10s | 5-30s | <1s |
| **Code quality** | 7/10 | 8/10 | 9/10 | 8/10 | 9/10 |
| **Context understanding** | 6/10 | 8/10 | 9/10 | 9/10 | 7/10 |
| **Accuracy** | 7/10 | 8/10 | 9/10 | 8/10 | 9/10 |
| **Learning curve** | Easy | Medium | Medium | Hard | Medium |
| **Integration effort** | Low | Medium | Medium | High | Medium |

---

## Conclusion

**There's no single "best" agent** - each excels at different tasks. RepoAgents lets you use multiple agents together, leveraging each one's strengths for optimal development experience.

**Recommended starting point**:
1. Start with **GitHub Copilot** for daily coding
2. Add **Gemini CLI** for reviews and docs (free tier)
3. Upgrade to **Claude** when you need deeper analysis
4. Add **Jules** or **OpenCode** based on specific needs

**Remember**: Update your `AGENTS.md` file as you learn what works best for your workflow!

---

## Resources

- [AGENTS.md Specification](https://agents.md/)
- [Setup Guide](./setup-guide.md)
- [GitHub Copilot Docs](https://docs.github.com/en/copilot)
- [Gemini API Docs](https://ai.google.dev/docs)
- [Claude API Docs](https://docs.anthropic.com/)
- [Jules Documentation](https://jules.google/)

Last updated: October 2025
