# OpenCode Rules - RepoAgents

## Project Overview
Template repository for integrating multiple AI coding agents into development workflows.

## Core Principles
1. **Code Quality First**: Prioritize maintainable, readable code
2. **Test-Driven**: Write tests before or alongside features
3. **Documentation**: Keep docs in sync with code
4. **Security**: Never commit secrets, validate inputs
5. **Consistency**: Follow established patterns

## Language & Framework
- **Primary**: TypeScript/JavaScript (Node.js)
- **Test Framework**: Jest
- **Style Guide**: Airbnb
- **Package Manager**: npm

## Code Style Rules

### TypeScript
```typescript
// ✅ DO: Use explicit types
function processRequest(data: RequestData): Promise<Response> {
  // implementation
}

// ❌ DON'T: Use implicit any
function processRequest(data) {
  // implementation
}
```

### Naming Conventions
- **Files**: `kebab-case.ts`
- **Classes/Interfaces**: `PascalCase`
- **Functions/Variables**: `camelCase`
- **Constants**: `UPPER_SNAKE_CASE`
- **Private properties**: `_prefixedCamelCase`

### Import Organization
```typescript
// 1. External dependencies
import { readFile } from 'fs/promises';
import axios from 'axios';

// 2. Internal modules
import { AgentConfig } from './types';
import { logger } from '../utils/logger';

// 3. Type-only imports
import type { Response } from './types';
```

## File Structure Rules

### Maximum Complexity
- Files: < 300 lines
- Functions: < 50 lines
- Cyclomatic complexity: < 10
- Nesting depth: < 4 levels

### Organization Pattern
```
feature/
├── index.ts              # Public exports
├── feature.ts            # Main logic
├── feature.test.ts       # Tests
├── feature.types.ts      # Type definitions
└── utils/                # Helper functions
    └── helper.ts
```

## Testing Rules

### Coverage Requirements
- Overall: > 80%
- New code: > 90%
- Critical paths: 100%

### Test Structure
```typescript
describe('ComponentName', () => {
  // Setup
  beforeEach(() => {
    // Initialize
  });

  describe('methodName', () => {
    it('should handle valid input correctly', () => {
      // Arrange
      const input = createValidInput();
      
      // Act
      const result = methodName(input);
      
      // Assert
      expect(result).toBeDefined();
    });

    it('should throw error for invalid input', () => {
      // Test error cases
      expect(() => methodName(null)).toThrow();
    });
  });

  // Cleanup
  afterEach(() => {
    // Clean up
  });
});
```

### Test File Naming
- Unit tests: `*.test.ts`
- Integration tests: `*.integration.test.ts`
- E2E tests: `*.e2e.test.ts`

## Error Handling

### Required Patterns
```typescript
// ✅ DO: Use custom error types
class ValidationError extends Error {
  constructor(message: string, public field: string) {
    super(message);
    this.name = 'ValidationError';
  }
}

// ✅ DO: Handle errors explicitly
try {
  await riskyOperation();
} catch (error) {
  if (error instanceof ValidationError) {
    logger.warn('Validation failed', { field: error.field });
  } else {
    logger.error('Unexpected error', { error });
  }
  throw error; // Re-throw or handle appropriately
}

// ❌ DON'T: Swallow errors silently
try {
  await riskyOperation();
} catch (error) {
  // Silent failure - BAD!
}
```

## Documentation Rules

### Required Documentation
1. All public APIs (functions, classes, interfaces)
2. Complex algorithms or business logic
3. Configuration files
4. Setup and deployment procedures

### JSDoc Format
```typescript
/**
 * Brief one-line description
 * 
 * Detailed description if needed, explaining the purpose,
 * behavior, and any important considerations.
 * 
 * @param paramName - Parameter description
 * @param options - Optional parameters
 * @returns Description of return value
 * @throws {ErrorType} When this error occurs
 * 
 * @example
 * ```typescript
 * const result = await functionName('value', { option: true });
 * ```
 */
```

### README Requirements
- Installation instructions
- Quick start guide
- API documentation or link
- Contributing guidelines
- License information

## Security Rules

### Never Commit
- API keys, tokens, passwords
- Private keys, certificates
- Database credentials
- Personal identifiable information (PII)

### Always Validate
```typescript
// ✅ DO: Validate and sanitize input
function processUserInput(input: string): string {
  if (typeof input !== 'string') {
    throw new ValidationError('Input must be a string');
  }
  
  if (input.length > MAX_LENGTH) {
    throw new ValidationError('Input exceeds maximum length');
  }
  
  return sanitize(input);
}
```

### Environment Variables
```typescript
// ✅ DO: Use environment variables for config
const config = {
  apiKey: process.env.API_KEY,
  apiUrl: process.env.API_URL || 'https://default.api.com'
};

// Validate required env vars
if (!config.apiKey) {
  throw new Error('API_KEY environment variable is required');
}
```

## Git Commit Rules

### Commit Message Format
```
[Component] Action: Brief description

Longer description if needed, explaining why this change
was made and any important context.

- Bullet points for multiple changes
- Keep lines under 72 characters

Closes #123
Relates to #456
```

### Examples
```
[Workflows] Add: Automated code review workflow
[Gemini] Fix: Configuration file path resolution
[Docs] Update: Setup guide with new agent instructions
[Tests] Refactor: Simplify mock data generation
```

## Pull Request Rules

### Before Creating PR
- [ ] All tests pass locally
- [ ] Code follows style guidelines
- [ ] Documentation updated
- [ ] No debugging code (console.log, etc.)
- [ ] Branch up to date with main
- [ ] Meaningful commit messages

### PR Description Template
```markdown
## What
Brief description of changes

## Why
Reason for the change

## How
Technical approach

## Testing
How to test the changes

## Screenshots
If UI changes

## Checklist
- [ ] Tests added/updated
- [ ] Docs updated
- [ ] No breaking changes (or documented)
```

## Dependencies

### Adding Dependencies
1. Evaluate necessity (vs. implementing ourselves)
2. Check bundle size impact
3. Review security advisories
4. Verify active maintenance
5. Document rationale

### Update Strategy
```bash
# Check for updates
npm outdated

# Update with care
npm update

# Audit security
npm audit
npm audit fix
```

## Performance Guidelines

### Async Operations
```typescript
// ✅ DO: Run independent operations in parallel
const [data1, data2, data3] = await Promise.all([
  fetchData1(),
  fetchData2(),
  fetchData3()
]);

// ❌ DON'T: Run in sequence unnecessarily
const data1 = await fetchData1();
const data2 = await fetchData2();
const data3 = await fetchData3();
```

### Avoid Premature Optimization
1. Write clear code first
2. Measure performance
3. Optimize bottlenecks
4. Re-measure to verify

## AI Agent Integration Specifics

### Agent Configuration Files
- Must be valid JSON/YAML/Markdown
- Include descriptive comments
- Follow provider-specific schema
- Test before committing

### Workflow Files
- Use descriptive names
- Add comments for complex logic
- Pin action versions
- Handle secrets securely

### Example Implementations
- Keep examples simple and focused
- Document purpose clearly
- Make them runnable
- Update with project changes

## Code Review Focus

When reviewing code, prioritize:
1. **Correctness**: Does it work as intended?
2. **Security**: Any vulnerabilities?
3. **Performance**: Any obvious bottlenecks?
4. **Maintainability**: Is it readable and well-structured?
5. **Tests**: Adequate coverage?
6. **Documentation**: Clear and up-to-date?

## Common Anti-Patterns to Avoid

```typescript
// ❌ Pyramid of Doom
doSomething(() => {
  doAnother(() => {
    doMore(() => {
      // Deep nesting
    });
  });
});

// ✅ Use async/await
await doSomething();
await doAnother();
await doMore();

// ❌ Magic Numbers
if (status === 200) { }

// ✅ Named Constants
const HTTP_OK = 200;
if (status === HTTP_OK) { }

// ❌ Mutation
const updateUser = (user) => {
  user.name = 'New Name';
  return user;
};

// ✅ Immutability
const updateUser = (user) => ({
  ...user,
  name: 'New Name'
});
```

## Resources
- Main instructions: `/AGENTS.md`
- Setup guide: `/docs/setup-guide.md`
- TypeScript docs: https://www.typescriptlang.org/
- Jest docs: https://jestjs.io/
- Airbnb style guide: https://github.com/airbnb/javascript
