```markdown
# Toonflow-app Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you the core development patterns and conventions used in the Toonflow-app repository, a TypeScript backend built with the Express framework. You'll learn how to structure files, write imports/exports, follow commit message standards, and understand the testing approach. This guide will help you contribute code that fits seamlessly into the project.

## Coding Conventions

### File Naming
- Use **PascalCase** for all file names.
  - Example: `UserController.ts`, `AuthService.ts`

### Import Style
- Use **relative imports** for referencing other files/modules.
  - Example:
    ```typescript
    import { UserService } from '../services/UserService';
    ```

### Export Style
- Use **named exports** for all modules.
  - Example:
    ```typescript
    export const getUser = () => { /* ... */ };
    export function createUser() { /* ... */ }
    ```

### Commit Messages
- Follow **conventional commit** style.
- Use prefixes like `chore`.
- Keep messages concise (average 48 characters).
  - Example:  
    ```
    chore: update dependencies for security patch
    ```

## Workflows

### Creating a New Feature
**Trigger:** When adding a new feature to the app  
**Command:** `/new-feature`

1. Create a new file using PascalCase (e.g., `NewFeature.ts`).
2. Use relative imports to include dependencies.
3. Export your functions or constants using named exports.
4. Write or update corresponding test files (`NewFeature.test.ts`).
5. Commit your changes using a conventional commit message.

### Refactoring Code
**Trigger:** When improving or restructuring existing code  
**Command:** `/refactor`

1. Identify the module to refactor.
2. Rename files if necessary, ensuring PascalCase is used.
3. Update all relative imports affected by the change.
4. Ensure all exports remain named exports.
5. Run tests to confirm no regressions.
6. Commit with a message like `chore: refactor [module] for clarity`.

### Writing Tests
**Trigger:** When adding or updating tests  
**Command:** `/write-test`

1. Create or update a test file matching the pattern `*.test.*` (e.g., `UserService.test.ts`).
2. Write tests for all exported functions.
3. Use the project's preferred testing framework (unknown, follow existing patterns).
4. Run tests to ensure correctness.
5. Commit with a message like `chore: add tests for [module]`.

## Testing Patterns

- Test files are named using the pattern `*.test.*` (e.g., `AuthService.test.ts`).
- Each exported function should have corresponding tests.
- The specific testing framework is not specified; follow the structure of existing test files.
- Place test files alongside the modules they test or in a dedicated test directory, as per existing patterns.

## Commands
| Command        | Purpose                                      |
|----------------|----------------------------------------------|
| /new-feature   | Scaffold a new feature following conventions |
| /refactor      | Refactor code while maintaining standards    |
| /write-test    | Add or update tests for a module             |
```
