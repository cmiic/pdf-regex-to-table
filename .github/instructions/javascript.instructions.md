---
applyTo: "**/*.{js,mjs,vue}"
---

# JavaScript / Vue instructions (ESLint)

## Goals

- Favor clear, maintainable code over clever tricks.
- Avoid unrelated refactors or style churn when touching JavaScript or Vue files.

## Linting and verification

- Always keep JavaScript and Vue changes **ESLint-clean** using the repo's flat config in `eslint.config.js`.
- Before finishing a change, run `npx eslint . --fix` (or `npx eslint path/to/file.js --fix`) and fix any remaining violations.
- This repo formats code via ESLint; prefer running `npx eslint . --fix` (or `npm run lint:js -- --fix` if available) or using your editor's ESLint integration over manual formatting.
- If ESLint reports errors, fix the underlying issues (or rerun `npm run lint:js -- --fix`) instead of weakening or disabling lint checks.
- Don't silence lint rules (e.g. `eslint-disable`) unless there's no reasonable alternative.

## Control flow and data safety

- Validate external or loosely typed data before treating it as trusted.
- Prefer early returns and small helpers over deeply nested conditionals.
- Keep async code explicit about failure paths; do not hide rejected states behind overly broad catch blocks.
- Check for `null` and `undefined` before use instead of assuming values exist.

## APIs and maintainability

- Keep functions small enough that their inputs, outputs, and side effects are easy to understand.
- Prefer plain objects, functions, and modules over classes unless a class clearly improves the design.
- Prefer reusing existing utilities and established patterns before creating near-duplicates — but not at the cost of clarity.
- Extract reusable helpers when logic is truly shared, repeated, or likely to drift if copied in multiple places.
- Keep exported APIs backward-compatible unless the task explicitly requires a breaking change.
- Avoid generic abstractions that are harder to read than the concrete code they replace.

## Practical workflow

- Change only the code relevant to the task.
- If a workaround depends on a framework invariant or external limitation, leave a brief comment explaining why.
