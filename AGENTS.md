# AGENTS.md - RepoAgents

## 🎯 Project Overview

**RepoAgents** is a template repository that demonstrates how to integrate multiple AI coding agents into any software project. It transforms a solo developer workflow into a full-team development experience through asynchronous collaboration with AI agents via GitHub Issues and Pull Requests.

This repository showcases configurations for:
- GitHub Copilot Workspace
- Google Gemini CLI
- Anthropic Claude
- OpenAI Codex
- OpenCode
- Google Jules
- Factory AI

## 🚀 Setup Commands

```bash
# Clone this repository (requires access)
git clone https://github.com/jorge-septeo/AI4Devs-finalproject.git
cd AI4Devs-finalproject

# Install dependencies (if needed)
npm install

# Run tests
npm test

# Build documentation
npm run docs
```

## 🏗️ Project Structure

```
/
├── AGENTS.md                 # This file - main agent instructions
├── .github/
│   ├── workflows/           # GitHub Actions for agent automation
│   └── ISSUE_TEMPLATE/      # Templates for agent interactions
├── agents/                  # Agent-specific configurations
│   ├── copilot/            # GitHub Copilot settings
│   ├── gemini/             # Gemini CLI configuration
│   ├── claude/             # Claude integration
│   ├── opencode/           # OpenCode rules
│   └── jules/              # Jules configuration
├── examples/               # Sample implementations
└── docs/                   # Documentation
```

## 💻 Development Guidelines

### Code Style
- Use TypeScript/JavaScript with ES6+ features
- Follow the Airbnb style guide
- Use functional programming patterns where possible
- Prefer composition over inheritance
- Write self-documenting code with meaningful variable names

### Naming Conventions
- **Files**: kebab-case (e.g., `agent-config.ts`)
- **Classes**: PascalCase (e.g., `AgentManager`)
- **Functions/Variables**: camelCase (e.g., `processAgentResponse`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `MAX_RETRY_ATTEMPTS`)

## 🧪 Testing Instructions

### Running Tests
```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage

# Run specific test file
npm test -- agents/copilot.test.ts
```

### Test Requirements
- Every new feature must include unit tests
- Maintain minimum 80% code coverage
- Include integration tests for agent workflows
- Test edge cases and error handling
- Mock external API calls to avoid rate limits

### Test Structure
```typescript
describe('AgentManager', () => {
  describe('processRequest', () => {
    it('should handle valid agent requests', () => {
      // Arrange
      // Act
      // Assert
    });
    
    it('should throw error for invalid configuration', () => {
      // Test error cases
    });
  });
});
```

## 📝 Documentation Standards

### Code Documentation
- Add JSDoc comments to all public functions and classes
- Include usage examples in documentation
- Document parameters, return types, and exceptions
- Keep README.md updated with new features

### Example JSDoc
```typescript
/**
 * Processes an agent request and returns the response
 * @param {AgentRequest} request - The agent request object
 * @param {AgentConfig} config - Configuration for the agent
 * @returns {Promise<AgentResponse>} The processed response
 * @throws {ValidationError} If request validation fails
 * @example
 * const response = await processAgentRequest(request, config);
 */
async function processAgentRequest(request, config) {
  // Implementation
}
```

## 🔄 Pull Request Guidelines

### PR Title Format
```
[Component] Brief description

Examples:
[Copilot] Add workspace configuration
[Docs] Update setup guide
[Workflows] Add code review automation
```

### PR Checklist
Before submitting a PR, ensure:
- [ ] All tests pass (`npm test`)
- [ ] Code follows style guidelines (`npm run lint`)
- [ ] Documentation is updated
- [ ] Commit messages are descriptive
- [ ] No console.logs or debugging code
- [ ] Branch is up to date with main

### Review Process
- PRs require at least one approval
- Address all review comments
- Keep PRs focused and small (< 400 lines when possible)
- Link related issues using "Closes #123" or "Relates to #456"

## 🐛 Issue Guidelines

### Bug Reports
Include:
- Clear description of the issue
- Steps to reproduce
- Expected vs actual behavior
- Environment details (OS, Node version, etc.)
- Screenshots or error logs if applicable

### Feature Requests
Include:
- Problem statement / use case
- Proposed solution
- Alternative solutions considered
- Impact on existing functionality

### Agent Task Format
When creating issues for agents to work on:
```markdown
## Task
[Clear description of what needs to be done]

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2

## Technical Notes
[Any technical constraints or suggestions]

## Files to Modify
- `path/to/file1.ts`
- `path/to/file2.ts`
```

## 🔒 Security Considerations

### API Keys and Secrets
- Never commit API keys or secrets
- Use environment variables for sensitive data
- Add sensitive files to `.gitignore`
- Use GitHub Secrets for CI/CD workflows

### Dependencies
- Regularly update dependencies (`npm audit`)
- Review security advisories
- Pin versions in production

## 🤖 Agent-Specific Instructions

### For GitHub Copilot
- Check `.github/copilot-instructions.md` for workspace-specific rules
- Use inline comments to guide code generation
- Leverage chat for architecture questions

### For Gemini CLI
- Configuration in `.gemini/settings.json`
- Use `contextFileName: "AGENTS.md"` for project context
- Refer to agent comparison docs for capabilities

### For Claude
- See `agents/claude/claude-config.md` for integration details
- Optimized for code review and refactoring tasks

### For OpenCode
- Rules defined in `agents/opencode/opencode-rules.md`
- Focus on code quality and best practices

### For Jules
- Configuration in `agents/jules/jules-config.md`
- Excellent for full-stack implementations

## 🎯 Common Agent Tasks

### Code Review
Agents should check for:
- Code style consistency
- Potential bugs or edge cases
- Performance considerations
- Security vulnerabilities
- Test coverage

### Test Generation
When generating tests:
- Follow existing test patterns
- Cover happy path and edge cases
- Use descriptive test names
- Include setup and teardown as needed

### Documentation
When updating docs:
- Keep language clear and concise
- Include code examples
- Update table of contents
- Check for broken links

### Feature Implementation
When implementing features:
1. Read related issues and PRs
2. Review existing code patterns
3. Write tests first (TDD when appropriate)
4. Implement feature
5. Update documentation
6. Create PR with clear description

## 📚 Additional Resources

- [AGENTS.md Specification](https://agents.md/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Testing Best Practices](./docs/testing-guide.md)
- [Agent Comparison Matrix](./docs/agent-comparison.md)

## 🤝 Contributing

This is an educational project (AI4Devs Final Project) demonstrating AI agent integration patterns and best practices. 

The repository is maintained for learning purposes. If you're interested in the concepts demonstrated here:
1. Review the agent configurations in `/agents/`
2. Study the GitHub Actions workflows
3. Check the documentation in `/docs/`
4. Use the patterns in your own projects

---

**Note**: This AGENTS.md file serves as the primary reference for all AI coding agents. Keep it updated as the project evolves.
