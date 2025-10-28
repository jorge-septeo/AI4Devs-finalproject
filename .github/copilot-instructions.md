# GitHub Copilot Workspace Instructions

## Project Context
This is **RepoAgents**, a template repository demonstrating AI agent integration for development workflows.

## Coding Preferences

### TypeScript/JavaScript
- Use TypeScript for new files
- Enable strict mode
- Prefer `const` over `let`, avoid `var`
- Use async/await over promises
- Prefer functional patterns and immutability

### Code Style
```typescript
// ✅ Good
const processAgent = async (config: AgentConfig): Promise<Result> => {
  const result = await agentService.process(config);
  return result;
};

// ❌ Avoid
function processAgent(config) {
  return agentService.process(config).then(function(result) {
    return result;
  });
}
```

## File Organization
- Group related files in feature folders
- Keep files small and focused (< 300 lines)
- Separate concerns (data, logic, presentation)

## Testing
- Write tests alongside code (co-located)
- Use descriptive test names
- Follow AAA pattern (Arrange, Act, Assert)
- Mock external dependencies

## Documentation
- Add JSDoc to all exported functions
- Include usage examples in complex functions
- Keep inline comments minimal and meaningful
- Update README when adding features

## Common Patterns

### Error Handling
```typescript
try {
  const result = await riskyOperation();
  return { success: true, data: result };
} catch (error) {
  logger.error('Operation failed', { error });
  return { success: false, error: error.message };
}
```

### API Response Format
```typescript
interface ApiResponse<T> {
  success: boolean;
  data?: T;
  error?: string;
  metadata?: Record<string, unknown>;
}
```

## Agent Workflow Integration
When working on agent-related features:
1. Check existing agent configurations in `/agents` folder
2. Follow the AGENTS.md guidelines
3. Test with multiple agent providers when possible
4. Update agent comparison docs

## Git Commit Messages
Format: `[Component] Action: Description`

Examples:
- `[Copilot] Add: Workspace configuration for TypeScript`
- `[Workflows] Fix: Code review automation trigger`
- `[Docs] Update: Setup guide with new agent`

## What to Avoid
- Don't commit commented-out code
- Don't use `any` type in TypeScript
- Don't create circular dependencies
- Don't bypass error handling
- Don't commit API keys or secrets

## Helpful Context Files
- `/AGENTS.md` - Main agent instructions
- `/docs/agent-comparison.md` - Agent capabilities
- `/.github/workflows/` - Automation examples
