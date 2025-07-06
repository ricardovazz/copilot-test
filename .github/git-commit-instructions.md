# Git Commit Instructions for GitHub Copilot

## Conventional Commits Format

All commit messages MUST follow the Conventional Commits 1.0.0 specification:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]

```

## Commit Types

Use these commit types for our Spring Boot 3 project:

- **feat**: A new feature (new REST endpoint, service method, entity)
- **fix**: A bug fix (error handling, validation fixes, logic corrections)
- **docs**: Documentation only changes (README, JavaDoc, API docs)
- **style**: Code style changes (formatting, missing semicolons, whitespace)
- **refactor**: Code changes that neither fix bugs nor add features
- **perf**: Performance improvements (query optimization, caching)
- **test**: Adding missing tests or correcting existing tests
- **chore**: Changes to build process, dependencies, or auxiliary tools
- **ci**: Changes to CI configuration files and scripts (GitHub Actions)
- **build**: Changes affecting build system or external dependencies (Maven, Docker)

## Scope Guidelines

Use these scopes for Spring Boot components:

- **controller**: REST controller changes
- **service**: Business logic layer changes
- **repository**: Data access layer changes
- **entity**: JPA entity and model changes
- **dto**: Data Transfer Object changes
- **config**: Configuration classes and properties
- **security**: Spring Security related changes
- **validation**: Input validation and constraints
- **exception**: Exception handling changes
- **test**: Test-related changes
- **migration**: Database migration scripts
- **api**: API contract changes

## Subject Line Rules

The subject line must:

- Use imperative, present tense: "change" not "changed" nor "changes"
- Not capitalize the first letter
- Not end with a period (.)
- Be limited to 50 characters maximum
- Be descriptive and concise

## Body Guidelines

When including a body:

- Use imperative, present tense: "change" not "changed" nor "changes"
- Include motivation for the change
- Contrast with previous behavior
- Wrap at 72 characters per line
- Separate from subject with a blank line

## Footer Requirements

The footer should contain:

- **Breaking Changes**: Start with "BREAKING CHANGE:" followed by description
- **Issue References**: Reference GitHub issues with "Closes #123" or "Fixes #456"
- **Co-authored-by**: For pair programming (Co-authored-by: Name <email@example.com>)

## Spring Boot Specific Examples

### Feature Commits
```

feat(controller): add user registration endpoint

Add POST /api/users endpoint for user registration with email validation
and password hashing using BCrypt

Closes \#45

```

### Bug Fix Commits
```

fix(service): handle null pointer in user validation

Add null check for user email field before validation to prevent
NullPointerException during user creation process

Fixes \#78

```

### Breaking Changes
```

feat(api): update user response format

Change user API response structure to include profile information
and deprecate legacy fields

BREAKING CHANGE: User API now returns profile object instead of
flat user properties. Update clients to use user.profile.name
instead of user.name

```

### Documentation Commits
```

docs(readme): update API documentation

Add examples for new user registration endpoint and update
authentication section with JWT token usage

```

### Test Commits
```

test(controller): add integration tests for user endpoints

Add comprehensive test coverage for user CRUD operations
including validation error scenarios and authentication tests

```

### Refactor Commits
```

refactor(service): simplify user validation logic

Extract common validation methods into utility class and
reduce code duplication across service methods

```

## Database Migration Commits
```

chore(migration): add user profile table

Add V2__Create_user_profile_table.sql migration script
to support extended user information storage

Related to \#123

```

## Configuration Commits
```

config(security): update CORS configuration

Allow requests from new frontend domain and update
allowed headers for API authentication

```

## Multiple Changes
When commit includes multiple related changes:
```

feat(user): implement user profile management

- Add user profile entity with validation
- Create profile service with CRUD operations
- Add profile REST endpoints with proper security
- Include integration tests for profile features

Closes \#34, \#67

```

## Commit Message Length Limits

- **Subject line**: Maximum 50 characters
- **Body lines**: Maximum 72 characters per line
- **Overall message**: No line longer than 100 characters

## Revert Commits

For reverting previous commits:
```

revert: feat(controller): add user registration endpoint

This reverts commit 1234567890abcdef.

Reason: Registration endpoint causing database connection issues
in production environment

```

## Co-authored Commits

For pair programming or collaborative work:
```

feat(service): implement user authentication

Add JWT token generation and validation service with
refresh token support and role-based access control

Co-authored-by: John Doe [john.doe@example.com](mailto:john.doe@example.com)
Co-authored-by: Jane Smith [jane.smith@example.com](mailto:jane.smith@example.com)

```

## Commit Verification

Before committing, ensure:

1. Run `git status` to verify you're on the correct branch
2. Use `git add <file>` to stage specific files
3. Use `git add -p` to stage partial changes
4. Verify commit message follows these guidelines
5. Check that all tests pass
6. Ensure code follows project style guidelines

## Tools Integration

This file works with:
- **JetBrains Copilot Prompt Plugin**: For generating commit messages
- **Commitizen**: Run `npm run commit` for interactive commit wizard
- **GitHub Copilot**: For commit message suggestions and validation
- **Conventional Changelog**: For automatic changelog generation

## Common Patterns to Avoid

❌ **Bad Examples**:
```

git commit -m "fixed bug"
git commit -m "Added new feature"
git commit -m "updated files"
git commit -m "WIP"

```

✅ **Good Examples**:
```

git commit -m "fix(validation): handle empty email input"
git commit -m "feat(auth): add JWT token refresh endpoint"
git commit -m "docs(api): update authentication examples"
git commit -m "test(service): add user service unit tests"

```

## Semantic Versioning Impact

Commit types correlate with semantic versioning:

- **fix**: PATCH version (1.0.1)
- **feat**: MINOR version (1.1.0)
- **BREAKING CHANGE**: MAJOR version (2.0.0)

These guidelines ensure consistent, readable commit history and enable automated tooling for changelog generation and semantic versioning.
```