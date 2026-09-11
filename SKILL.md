---
name: dti-design-frontend
description: Help designers implement focused frontend changes in existing DTI product repositories using each product's design system and conventions. Use when translating Figma designs or visual feedback into code, validating the implementation, or preparing work for human review. Do not use for backend work or broad architecture changes.
---

# DTI Design Frontend

Help a designer turn a defined visual change into a small, understandable frontend implementation. Adapt to the current product instead of assuming that every DTI repository uses the same framework, commands, or design system.

## Working agreement

- The designer owns the design intent and decides whether the result is visually correct.
- The agent may inspect and summarize the diff, but the designer must review and approve it.
- The designer decides when to involve a TPM or engineer. The agent should identify the concern and suggest a concrete question for the designer to raise; it must not contact anyone unless the user explicitly requests and authorizes that action.
- Do not commit, push, open a pull request, merge, or deploy unless the user explicitly asks for that action.

## Product context

Before editing, inspect the repository for the context that changes implementation decisions:

- `AGENTS.md`, `README.md`, and other repository instructions
- `docs/dti-design-frontend.md`, when present
- Package scripts and local setup documentation
- Existing feature code and nearby implementations
- Design-system components, tokens, variants, and documentation

Treat current repository instructions and the user's request as authoritative. Do not invent commands, component APIs, tokens, or ownership rules.

When the user asks to prepare this skill for a new product, read [references/product-profile-template.md](references/product-profile-template.md). Use it to propose or create `docs/dti-design-frontend.md` only when the user requests that repository change.

## Workflow

### Understand the change

Identify the design reference, desired behavior, relevant states, screen sizes, and explicit non-goals. If a linked design cannot be accessed, request a screenshot or written acceptance criteria before making visually specific decisions.

### Locate the implementation

Trace the visible UI through the page or route, feature component, design-system component, variant, and token. Inspect nearby code to learn the product's established pattern before adding a new abstraction or custom style.

### Assess the boundary

Proceed with a focused implementation when the change uses established patterns and preserves product behavior. Examples include local layout, component composition, existing props or variants, tokens, typography, responsive styling, and visual states.

Flag the issue for human discussion before implementation when the request appears to require:

- New or changed API behavior
- Authentication or permission changes
- New application state or data-model behavior
- A change to a widely shared component
- A large design-system addition or breaking variant change
- Product behavior that the design does not define

Explain why the issue matters and give the designer a specific question to take to the TPM or engineer.

### Implement the change

- Reuse existing components, tokens, and variants when they satisfy the design.
- Prefer patterns already used in the same product.
- Keep the change limited to the requested UI.
- Preserve application logic and unrelated behavior.
- Avoid adding dependencies or changing global configuration unless the task clearly requires it.
- Protect existing user changes in the working tree.
- State any assumption that affects appearance, behavior, or scope.

For a small, well-defined task, briefly state the approach and continue. Pause only when a missing decision would materially change the result or expand the task beyond a focused frontend change.

### Verify the implementation

Use commands defined by the repository to run relevant formatting, type checks, tests, or builds. When a local preview is available, verify the affected states and screen sizes against the design reference. Check accessibility when the change affects semantics, focus, keyboard interaction, labels, or contrast.

Do not claim that automated checks prove visual correctness.

### Prepare human review

Inspect the diff and present it to the designer in plain language. Highlight:

- Files changed and the purpose of each change
- Visual states and screen sizes checked
- Automated checks run and their results
- Assumptions, risks, or behavior that could not be verified
- Unexpected, shared, or non-visual changes that deserve extra attention

The designer performs the final diff review. Wait for explicit direction before taking any requested Git or pull-request action.

## Expected handoff

When the implementation is complete, provide a compact summary, verification results, and clear items for human review. If the user asks for a pull-request draft, include a suggested title, description, test plan, design reference, and any open questions.
