# 📏 Coding Standards & Best Practices

[![ClawHub Skill](https://img.shields.io/badge/ClawHub-Skill-blue)](https://clawhub.ai/djc00p/coding-standards) [![Agent Skill](https://img.shields.io/badge/Agent-Skill-blue)](#) [![TypeScript](https://img.shields.io/badge/TypeScript-3178C6.svg)](https://www.typescriptlang.org/) [![React](https://img.shields.io/badge/React-20232A.svg)](https://react.dev) [![Node.js](https://img.shields.io/badge/Node.js-5FA04E.svg)](https://nodejs.org) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Coding Standards** is a set of universal, opinionated conventions for maintainable TypeScript, JavaScript, React, and Node.js code.

The rules here are deliberately few. Each one earns its place by preventing a specific, recurring failure — not by expressing taste. When a standard exists, it exists because the alternative showed up in production.

---

## 🧭 Core Principles

**KISS** — the simplest solution that works. No premature optimization.

**DRY** — extract common logic into reusable functions and components.

**YAGNI** — don't build before it's needed. Start simple, refactor when needed.

**Readability** — code is read 10x more than written. Clarity over cleverness.

---

## ✅ Quick Start

1. **Readability First** — clear names, self-documenting code
2. **Type Safety** — avoid `any`, use explicit interfaces
3. **Error Handling** — try-catch with specific error types
4. **Immutability** — use the spread operator, never direct mutation
5. **Test Structure** — AAA pattern (Arrange, Act, Assert)

---

## 🏷️ Naming Standards

### Variables

```typescript
// Good: Descriptive, type-hinted by name
const marketSearchQuery = 'election'
const isUserAuthenticated = true
const totalRevenue = 1000

// Bad: Single-letter, unclear
const q = 'election'
const flag = true
const x = 1000
```

The `is` prefix on booleans and the domain noun on everything else means a reader can infer the type from the name alone.

### Functions

```typescript
// Good: Verb-noun pattern
async function fetchMarketData(id: string) { }
function calculateSimilarity(a: number[], b: number[]) { }
function isValidEmail(email: string): boolean { }

// Bad: Unclear or noun-only
async function market(id: string) { }
function similarity(a, b) { }
function email(e) { }
```

---

## 🧪 Testing Patterns

The **AAA** structure — Arrange, Act, Assert — keeps tests readable and makes failures obvious:

```typescript
test('rejects invalid email format', () => {
  // Arrange
  const invalidEmail = 'not-an-email'

  // Act
  const result = validateEmail(invalidEmail)

  // Assert
  expect(result.isValid).toBe(false)
})
```

---

## 🚨 Code Smells to Catch

| Smell | Signal |
|-------|--------|
| **Long functions** | One function doing five things |
| **Deep nesting** | Four or more levels of conditionals |
| **Magic numbers** | `if (status === 3)` with no named constant |
| **Unused code** | Exported but never imported |
| **Boolean parameter trap** | `process(data, true)` — what does `true` mean? |
| **Too many parameters** | Six or more arguments |
| **Inconsistent naming** | `getUser` and `fetch_customer` in the same file |
| **Tight coupling** | A change in one module breaks three others |
| **Incomplete error handling** | A `catch` block that swallows the error |

---

## 📁 File Organization

* **Project structure** — group by feature or by layer, but pick one and stay consistent
* **File naming** — match the existing convention; don't mix `kebab-case` and `snake_case`
* **Collocate related files** — a component lives next to its test and its styles
* **Constants organization** — one constants module, not scattered literals
* **Imports** — group and order them; let the linter handle the mechanical part

---

## 🔌 API Design

REST conventions, input validation, and consistent error responses:

```text
GET    /api/v1/users/:id
POST   /api/v1/users
PATCH  /api/v1/users/:id
DELETE /api/v1/users/:id
```

* Query parameters for filtering, not path segments
* Consistent response envelope across every endpoint
* Validate input at the boundary — never trust the client
* Return the same error shape every time

---

## ⚛️ React Best Practices

* **Component structure** — one component per file, single responsibility
* **Custom hooks** — extract reusable stateful logic, name it `useSomething`
* **State management** — local state first; lift only when siblings need it
* **Memoization** — `useMemo`/`useCallback` for genuinely expensive work, not by default

---

## 📚 References

* `references/typescript.md` — type safety, immutability, async patterns
* `references/react.md` — component structure, hooks, state management
* `references/api-design.md` — REST conventions, validation, error responses
* `references/file-org.md` — project structure, file naming
* `references/testing.md` — test patterns, AAA structure, test naming
* `references/code-smells.md` — anti-patterns, long functions, deep nesting, magic numbers

---

**Adapted from [everything-claude-code](https://github.com/affanm/everything-claude-code) by [@affaan-m](https://github.com/affaan-m) (MIT).**

**Published by [@djc00p](https://github.com/djc00p)**
