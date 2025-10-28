# Claude Agent Configuration

## Project: RepoAgents
AI agent integration template for development workflows.

## Primary Role
Claude excels at:
- Code review and refactoring
- Architecture analysis and suggestions
- Complex problem-solving
- Documentation improvement
- Test coverage analysis

## Context Files
Always reference these files:
1. `/AGENTS.md` - Primary project instructions
2. `/README.md` - Project overview and setup
3. `/docs/agent-comparison.md` - Agent capabilities matrix

## Code Review Guidelines

### Focus Areas
- **Code Quality**: Clean code principles, SOLID, DRY
- **Performance**: Algorithmic complexity, potential bottlenecks
- **Security**: Input validation, API key handling, injection risks
- **Maintainability**: Code readability, documentation, modularity
- **Testing**: Coverage gaps, edge cases, test quality

### Review Template
```markdown
## Code Review Summary
- **Overall Quality**: [Score/10]
- **Key Strengths**: [List 2-3 strengths]
- **Areas for Improvement**: [List priority issues]

## Detailed Findings

### 🔴 Critical Issues
[Issues that must be fixed]

### 🟡 Suggestions
[Nice-to-have improvements]

### 🟢 Positive Aspects
[What's done well]

## Recommendations
[Actionable next steps]
```

## Refactoring Approach

### Before Refactoring
1. Understand the current implementation
2. Identify code smells
3. Ensure tests exist
4. Plan changes incrementally

### Refactoring Patterns
- Extract functions for complex logic
- Simplify conditional expressions
- Remove duplication
- Improve naming
- Separate concerns

### After Refactoring
- Verify all tests pass
- Confirm no behavior changes
- Update documentation
- Add tests if coverage decreased

## Implementation Strategy

### For New Features
1. **Understand Requirements**
   - Read issue description thoroughly
   - Identify acceptance criteria
   - Check for related code

2. **Design Solution**
   - Consider multiple approaches
   - Evaluate trade-offs
   - Choose simplest effective solution

3. **Write Tests First** (when appropriate)
   - Define expected behavior
   - Cover edge cases
   - Use TDD for complex logic

4. **Implement Feature**
   - Follow project conventions
   - Keep changes focused
   - Add inline documentation

5. **Verify & Document**
   - Run all tests
   - Update relevant docs
   - Add usage examples

## Communication Style

### In Pull Requests
- Be constructive and specific
- Explain the "why" not just "what"
- Suggest alternatives when criticizing
- Acknowledge good practices
- Ask clarifying questions

### In Issue Responses
- Provide comprehensive analysis
- Break down complex tasks
- Offer implementation guidance
- Link to relevant documentation
- Estimate complexity when helpful

## TypeScript Preferences
```typescript
// Prefer explicit types
interface AgentConfig {
  name: string;
  provider: AgentProvider;
  capabilities: string[];
}

// Use type guards
function isValidConfig(config: unknown): config is AgentConfig {
  return (
    typeof config === 'object' &&
    config !== null &&
    'name' in config &&
    'provider' in config
  );
}

// Leverage utility types
type PartialConfig = Partial<AgentConfig>;
type ReadonlyConfig = Readonly<AgentConfig>;
```

## Error Handling Pattern
```typescript
// Use Result type for operations that can fail
type Result<T, E = Error> = 
  | { success: true; value: T }
  | { success: false; error: E };

async function processAgent(config: AgentConfig): Promise<Result<Response>> {
  try {
    const response = await agentAPI.process(config);
    return { success: true, value: response };
  } catch (error) {
    return { 
      success: false, 
      error: error instanceof Error ? error : new Error(String(error))
    };
  }
}
```

## Documentation Standards

### Function Documentation
```typescript
/**
 * Processes an agent request with the specified configuration.
 * 
 * @param config - Agent configuration including provider and capabilities
 * @param options - Optional processing parameters
 * @returns Promise resolving to the agent's response
 * @throws {ValidationError} If configuration is invalid
 * @throws {APIError} If the agent API call fails
 * 
 * @example
 * ```typescript
 * const config: AgentConfig = {
 *   name: 'code-reviewer',
 *   provider: 'claude',
 *   capabilities: ['review', 'refactor']
 * };
 * 
 * const result = await processAgent(config);
 * if (result.success) {
 *   console.log(result.value);
 * }
 * ```
 */
```

## Agent Workflow Integration

### When Reviewing PRs
1. Check PR description for context
2. Review changed files systematically
3. Test changes locally if needed
4. Provide inline comments on specific lines
5. Summarize review in PR comment

### When Implementing Features
1. Reference the issue number
2. Follow acceptance criteria
3. Update tests
4. Document new functionality
5. Create focused, reviewable PR

## Project-Specific Context

### Key Directories
- `/agents/` - Agent-specific configurations
- `/.github/workflows/` - Automation workflows
- `/examples/` - Sample implementations
- `/docs/` - Project documentation

### Core Technologies
- TypeScript/Node.js
- GitHub Actions
- Multiple AI provider APIs
- Markdown for documentation

### Quality Thresholds
- Test coverage: > 80%
- TypeScript strict mode: enabled
- No `any` types without justification
- All functions documented

## Best Practices Reminders
- Read AGENTS.md before starting tasks
- Keep PRs small and focused
- Test thoroughly before requesting review
- Update documentation alongside code
- Consider security implications
- Think about edge cases
- Optimize for readability over cleverness
