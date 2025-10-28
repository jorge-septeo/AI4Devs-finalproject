# Jules Configuration - RepoAgents

## Project Information
**Name**: RepoAgents  
**Type**: Template Repository  
**Purpose**: Demonstrate AI agent integration for development workflows  
**Tech Stack**: TypeScript/Node.js, GitHub Actions, Multiple AI Providers

## Jules Primary Capabilities
Jules from Google excels at:
- Full-stack feature implementation
- End-to-end workflow automation
- Multi-file refactoring
- Integration testing
- Complex architectural changes

## Project Context

### What is RepoAgents?
A template repository that enables solo developers to work with AI coding agents as if they had a full development team. Agents collaborate asynchronously through GitHub Issues and Pull Requests.

### Supported Agents
- GitHub Copilot Workspace
- Google Gemini CLI
- Anthropic Claude
- OpenAI Codex
- OpenCode
- Jules (this configuration)
- Factory AI

### Key Files
- `AGENTS.md` - Main agent instructions (READ FIRST)
- `.github/copilot-instructions.md` - Copilot workspace config
- `agents/*/` - Agent-specific configurations
- `.github/workflows/` - Automation workflows

## Development Environment

### Prerequisites
```bash
# Node.js v18 or higher
node --version

# npm v9 or higher
npm --version
```

### Setup
```bash
# Install dependencies
npm install

# Run tests
npm test

# Start development
npm run dev
```

### Project Structure
```
/
├── AGENTS.md                    # Main agent instructions
├── README.md                    # Project documentation
├── prompts.md                   # AI prompt documentation
├── .github/
│   ├── copilot-instructions.md
│   └── workflows/              # GitHub Actions
├── agents/                     # Agent configurations
│   ├── copilot/
│   ├── gemini/
│   ├── claude/
│   ├── opencode/
│   └── jules/                  # This directory
├── examples/                   # Sample implementations
├── docs/                       # Documentation
└── tests/                      # Test files
```

## Coding Standards

### TypeScript Configuration
```json
{
  "compilerOptions": {
    "strict": true,
    "target": "ES2022",
    "module": "commonjs",
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true
  }
}
```

### Style Guidelines
- **Indentation**: 2 spaces
- **Quotes**: Single quotes for strings
- **Semicolons**: Not required (but consistent)
- **Line Length**: Max 100 characters
- **File Naming**: kebab-case

### Code Patterns
```typescript
// Prefer functional components and pure functions
const processAgentRequest = (request: AgentRequest): Result => {
  // Implementation
};

// Use discriminated unions for better type safety
type Result<T> = 
  | { status: 'success'; data: T }
  | { status: 'error'; error: Error };

// Leverage async/await
async function executeWorkflow(workflow: Workflow): Promise<Result<Output>> {
  try {
    const result = await workflowEngine.execute(workflow);
    return { status: 'success', data: result };
  } catch (error) {
    return { status: 'error', error: error as Error };
  }
}
```

## Testing Strategy

### Test Framework: Jest
```bash
# Run all tests
npm test

# Watch mode
npm run test:watch

# Coverage report
npm run test:coverage

# Specific test file
npm test -- jules-integration.test.ts
```

### Test Organization
```typescript
// jules-integration.test.ts
import { JulesAgent } from './jules-agent';
import { mockGitHubAPI } from '../__mocks__/github';

describe('JulesAgent Integration', () => {
  let agent: JulesAgent;

  beforeEach(() => {
    agent = new JulesAgent({
      apiKey: 'test-key',
      repository: 'jorge-septeo/AI4Devs-finalproject'
    });
  });

  describe('Feature Implementation', () => {
    it('should implement feature from issue description', async () => {
      const issue = {
        number: 1,
        title: 'Add agent configuration validator',
        body: 'Create a function to validate agent config files'
      };

      const result = await agent.implementFeature(issue);

      expect(result.status).toBe('success');
      expect(result.filesCreated).toContain('src/validators/agent-config.ts');
      expect(result.testsAdded).toBeGreaterThan(0);
    });

    it('should handle complex multi-file changes', async () => {
      // Test implementation
    });
  });

  describe('Code Review', () => {
    it('should provide comprehensive PR review', async () => {
      // Test implementation
    });
  });

  afterEach(() => {
    mockGitHubAPI.reset();
  });
});
```

### Coverage Requirements
- Minimum overall: 80%
- New features: 90%
- Critical paths: 100%

## Feature Implementation Workflow

### 1. Understand the Requirement
```typescript
// Read issue thoroughly
interface Issue {
  number: number;
  title: string;
  body: string;
  labels: string[];
  assignees: string[];
}

// Extract requirements
const extractRequirements = (issue: Issue): Requirements => {
  // Parse acceptance criteria
  // Identify technical constraints
  // List affected components
};
```

### 2. Plan the Implementation
- Identify files to create/modify
- Design data structures
- Plan test strategy
- Consider edge cases
- Review existing patterns

### 3. Implement Feature
```typescript
// Create feature files
// src/features/agent-validator/
//   ├── index.ts           # Public exports
//   ├── validator.ts       # Main logic
//   ├── validator.test.ts  # Unit tests
//   ├── types.ts           # Type definitions
//   └── utils/             # Helpers

// Follow TDD when appropriate
// 1. Write failing test
// 2. Implement minimum code to pass
// 3. Refactor
// 4. Repeat
```

### 4. Documentation
```typescript
/**
 * Validates agent configuration against schema
 * 
 * Ensures all required fields are present and valid,
 * checks provider-specific requirements, and validates
 * capability specifications.
 * 
 * @param config - Agent configuration object to validate
 * @param options - Validation options
 * @returns Validation result with errors if any
 * 
 * @example
 * ```typescript
 * const config = {
 *   name: 'code-reviewer',
 *   provider: 'claude',
 *   capabilities: ['review', 'refactor']
 * };
 * 
 * const result = validateAgentConfig(config);
 * if (!result.valid) {
 *   console.error('Invalid config:', result.errors);
 * }
 * ```
 */
export function validateAgentConfig(
  config: AgentConfig,
  options?: ValidationOptions
): ValidationResult {
  // Implementation
}
```

### 5. Create Pull Request
```markdown
## Feature: Agent Configuration Validator

### What
Implements validation for agent configuration files to ensure they meet schema requirements before processing.

### Why
Prevents runtime errors from invalid configurations and provides clear feedback to users about what needs to be fixed.

### How
- Created `AgentConfigValidator` class with schema validation
- Added support for all agent providers (Copilot, Gemini, Claude, etc.)
- Included comprehensive error messages
- Added 15 unit tests covering edge cases

### Testing
```bash
npm test -- agent-validator
```

### Files Changed
- `src/validators/agent-config.ts` (new)
- `src/validators/agent-config.test.ts` (new)
- `src/types/agent.ts` (updated with ValidationResult type)
- `docs/validation.md` (new)

### Checklist
- [x] Tests pass
- [x] Coverage > 90%
- [x] Documentation updated
- [x] No breaking changes
- [x] Follows code style
```

## GitHub Integration

### Issue Handling
```typescript
// Respond to issues with implementation plan
interface IssueResponse {
  plan: ImplementationPlan;
  estimate: string;
  questions?: string[];
  risks?: string[];
}

// Example response
const planResponse: IssueResponse = {
  plan: {
    steps: [
      'Create validator class with schema definition',
      'Implement validation logic for each provider',
      'Add comprehensive error messages',
      'Write unit tests',
      'Update documentation'
    ],
    filesAffected: [
      'src/validators/agent-config.ts',
      'src/types/agent.ts',
      'docs/validation.md'
    ]
  },
  estimate: '2-3 hours',
  questions: [
    'Should we validate capability availability per provider?',
    'Do we need to support custom validation rules?'
  ]
};
```

### Pull Request Reviews
Focus areas for reviews:
1. **Correctness**: Does it solve the stated problem?
2. **Code Quality**: Clean, readable, maintainable?
3. **Tests**: Adequate coverage and quality?
4. **Performance**: Any obvious bottlenecks?
5. **Security**: Input validation, no secrets?
6. **Documentation**: Clear and complete?

### Automation Workflows
Jules can trigger and interact with GitHub Actions:
```yaml
# .github/workflows/jules-integration.yml
name: Jules Agent Integration

on:
  issue_comment:
    types: [created]

jobs:
  process-command:
    if: contains(github.event.comment.body, '@jules')
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Process Jules Command
        run: |
          # Parse command
          # Execute action
          # Comment back with results
```

## Best Practices for Jules

### Multi-File Changes
When implementing features that span multiple files:
1. Start with type definitions
2. Implement core logic
3. Add tests
4. Update documentation
5. Verify all files work together

### Refactoring
When refactoring:
1. Ensure comprehensive tests exist
2. Make changes incrementally
3. Verify tests pass after each change
4. Document what changed and why
5. Update any affected documentation

### Complex Features
For complex implementations:
1. Break into smaller tasks
2. Implement incrementally
3. Test each component
4. Integrate step by step
5. Add integration tests

## Error Handling

### Standard Error Pattern
```typescript
class AgentError extends Error {
  constructor(
    message: string,
    public code: string,
    public context?: Record<string, unknown>
  ) {
    super(message);
    this.name = 'AgentError';
  }
}

// Usage
throw new AgentError(
  'Failed to validate configuration',
  'VALIDATION_ERROR',
  { config, errors: validationErrors }
);
```

### Error Recovery
```typescript
async function robustOperation<T>(
  operation: () => Promise<T>,
  options: { retries?: number; backoff?: number } = {}
): Promise<T> {
  const { retries = 3, backoff = 1000 } = options;
  
  for (let i = 0; i < retries; i++) {
    try {
      return await operation();
    } catch (error) {
      if (i === retries - 1) throw error;
      await sleep(backoff * Math.pow(2, i));
    }
  }
  
  throw new Error('Should not reach here');
}
```

## Security Considerations

### API Key Handling
```typescript
// ✅ DO: Use environment variables
const apiKey = process.env.JULES_API_KEY;
if (!apiKey) {
  throw new Error('JULES_API_KEY not configured');
}

// ❌ DON'T: Hardcode keys
const apiKey = 'sk-1234567890'; // NEVER DO THIS
```

### Input Validation
```typescript
// Always validate external input
function processWebhook(payload: unknown): WebhookData {
  if (!isValidWebhook(payload)) {
    throw new ValidationError('Invalid webhook payload');
  }
  
  return sanitizeWebhookData(payload);
}
```

## Performance Optimization

### Caching Strategy
```typescript
// Cache expensive operations
const cache = new Map<string, CacheEntry>();

async function getAgentConfig(name: string): Promise<AgentConfig> {
  const cached = cache.get(name);
  if (cached && !isCacheExpired(cached)) {
    return cached.data;
  }
  
  const config = await loadAgentConfig(name);
  cache.set(name, { data: config, timestamp: Date.now() });
  return config;
}
```

### Parallel Processing
```typescript
// Process multiple agents in parallel
async function validateAllAgents(
  agents: string[]
): Promise<ValidationResult[]> {
  return await Promise.all(
    agents.map(agent => validateAgent(agent))
  );
}
```

## Resources & References

### Project Documentation
- `/AGENTS.md` - Main instructions
- `/README.md` - Project overview
- `/docs/setup-guide.md` - Setup instructions
- `/docs/agent-comparison.md` - Agent capabilities

### External Resources
- [Jules Documentation](https://jules.google/)
- [GitHub API](https://docs.github.com/en/rest)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [Jest Documentation](https://jestjs.io/)

### Code Examples
- `/examples/` - Sample implementations
- `/tests/` - Test examples

## Communication Guidelines

### Issue Comments
Be clear, concise, and actionable:
```markdown
I'll implement this feature with the following approach:

1. **Configuration Validator** (`src/validators/agent-config.ts`)
   - Schema validation for all providers
   - Detailed error messages
   - Support for custom rules

2. **Type Definitions** (`src/types/validation.ts`)
   - ValidationResult interface
   - Error type definitions

3. **Tests** (`src/validators/agent-config.test.ts`)
   - Unit tests for each provider
   - Edge case coverage
   - Integration tests

**Estimate**: 2-3 hours  
**Questions**: Should we validate capability availability per provider?

I'll create a PR when complete.
```

### Pull Request Comments
Provide context and guidance:
```markdown
## Implementation Notes

This PR implements agent configuration validation as requested in #123.

**Key Changes**:
- New validator with comprehensive schema checks
- Support for all 7 agent providers
- 95% test coverage

**Testing**:
```bash
npm test -- agent-validator
```

**Documentation**: Updated in `/docs/validation.md`

Ready for review @maintainer
```

---

**Note**: This configuration is optimized for Jules' capabilities in full-stack development and complex feature implementation. Always refer to `/AGENTS.md` for project-wide guidelines.
