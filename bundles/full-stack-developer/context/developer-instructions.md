# Developer Instructions

## Development Workflow Best Practices

### Code Quality First

1. **Before writing code**: Understand the existing codebase patterns
2. **While writing code**: Follow established conventions and type safety
3. **After writing code**: Run quality checks before committing

### Git Workflow Patterns

#### Commit Guidelines

- Write clear, descriptive commit messages
- Use conventional commits format: `type(scope): description`
  - `feat`: New feature
  - `fix`: Bug fix
  - `refactor`: Code refactoring
  - `docs`: Documentation changes
  - `test`: Adding or updating tests
  - `chore`: Maintenance tasks

#### Branch Strategy

- Create feature branches from main: `feature/description`
- Use fix branches for bugs: `fix/issue-description`
- Keep branches focused and short-lived

#### Pull Request Best Practices

- Provide clear PR descriptions explaining the "why"
- Link related issues
- Request reviews from appropriate team members
- Address feedback promptly

### Code Quality Checks

#### TypeScript/JavaScript

- Run type checking before commits
- Ensure no ESLint errors or warnings
- Follow project formatting standards (Prettier/ESLint)

#### Python

- Use type hints for function signatures
- Run `ruff` for linting and formatting
- Run `pyright` for type checking
- Ensure all tests pass with `pytest`

### Testing Standards

1. **Unit tests**: Test individual functions and components
2. **Integration tests**: Test component interactions
3. **E2E tests**: Test critical user workflows

### Memory and Context

- Use memory tools to persist important project decisions
- Document architectural choices for future reference
- Maintain context across sessions for complex tasks

### Safety Guidelines

- Never commit secrets or credentials
- Review file changes before committing
- Use `.gitignore` for local configuration
- Backup important changes before destructive operations
