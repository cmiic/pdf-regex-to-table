---
applyTo: "**/*.{ts,tsx,d.ts,vue}"
---

# TypeScript instructions (ESLint + tsc)

## Goals

- Favor clear, maintainable, type-safe code over clever type tricks.
- Use types to make runtime behavior easier to understand, not harder.
- Avoid unrelated refactors or style churn when touching TypeScript files.

## Linting and verification

- Always keep TypeScript changes **ESLint-clean** using the repo's flat config in `eslint.config.js`.
- Before finishing a TS change, run `npx eslint . --fix` (or `npx eslint path/to/file.ts --fix`) and fix any remaining violations.
- Always keep TypeScript changes **typecheck-clean** using `npm run typecheck` (runs `tsc -p tsconfig.json`).
- This repo formats TypeScript via ESLint (see `.vscode/settings.json`); prefer `source.fixAll.eslint` over manual formatting.
- If ESLint or typecheck fails because generated Nuxt files are missing, run `npx nuxt prepare` or `npm ci` instead of weakening the checks.
- Don't silence rules (for example `eslint-disable`) unless there's no reasonable alternative.
- Avoid `@ts-ignore`. If a suppression is truly unavoidable, prefer `@ts-expect-error` with a short reason and make sure the error is intentional.

## Type quality

- Don't use `any` unless there's no reasonable alternative; prefer `unknown` plus narrowing or validation.
- Prefer explicit types at module boundaries such as exported functions, public helpers, props, emits, and return values when inference is not obvious.
- Let TypeScript infer straightforward local variables when the inferred type is already clear.
- Model domain shapes with named types or interfaces when they are reused or important to understand.
- Prefer discriminated unions and precise literal types over loose strings, booleans, or parallel optional fields.
- Use `readonly` when values or arrays should not be mutated after creation.
- Prefer `import type { ... }` for type-only imports.

## Control flow and data safety

- Narrow `null`, `undefined`, and union types before use instead of asserting them away.
- Avoid non-null assertions (`!`) unless the invariant is immediate and obvious from nearby code.
- Validate external or loosely typed data before treating it as a trusted application type.
- Prefer early returns and small helpers over deeply nested conditionals.
- Keep async code explicit about failure paths; do not hide rejected states behind overly broad catch blocks.

## APIs and maintainability

- Keep functions small enough that their inputs, outputs, and side effects are easy to understand.
- Prefer plain objects, functions, and modules over classes unless a class clearly improves the design.
- Prefer reusing existing utilities, shared types, and established patterns before creating near-duplicates — but not at the cost of clarity.
- Extract reusable helpers or types when logic is truly shared, repeated, or likely to drift if copied in multiple places.
- Keep exported APIs backward-compatible unless the task explicitly requires a breaking change.
- Avoid generic abstractions that are harder to read than the concrete code they replace.

## Declaration files

- In `.d.ts` files, keep declarations minimal, accurate, and free of runtime code.
- Use module augmentation only when needed and keep the augmentation narrowly scoped.
- Make ambient declarations specific enough that they do not accidentally loosen type safety across the project.

## Practical workflow

- Change only the TypeScript relevant to the task.
- Keep new types close to their usage unless they are genuinely shared.
- If a workaround depends on a framework invariant or external limitation, leave a brief comment explaining why.
