# DTI Design Frontend

An Agent Skill for designers making focused frontend changes in an existing product repository. It helps an AI coding agent find the right implementation, follow the product's design system, keep the change scoped, verify the result, and prepare it for human review.

## What it helps with

- Translating a Figma design or visual feedback into frontend code
- Reusing existing components, tokens, variants, and product patterns
- Making contained layout, typography, responsive, and interaction changes
- Running the repository's existing checks and preview workflow
- Flagging work that may need a TPM or engineer before it expands in scope

This skill is not intended for backend work, authentication changes, data-model changes, or broad architecture work.

## Install in Codex

The easiest option is to ask Codex to install it from this repository:

```text
$skill-installer Install the skill from https://github.com/zw757/dti-design-frontend
```

Codex detects installed skills automatically. Restart Codex if it does not appear.

For a manual user-level installation, clone the repository into your skills folder:

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/zw757/dti-design-frontend ~/.agents/skills/dti-design-frontend
```

To make the skill available only within one product repository, place it at:

```text
<product-repository>/.agents/skills/dti-design-frontend/
```

## Install in Claude Code

For a personal installation available across your Claude Code projects:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/zw757/dti-design-frontend ~/.claude/skills/dti-design-frontend
```

To share the skill with everyone working in one product repository, copy its contents into the repository and commit them at:

```text
<product-repository>/.claude/skills/dti-design-frontend/
```

Claude Code can select the skill automatically when a request matches its description. You can also invoke it directly:

```text
/dti-design-frontend Implement the linked Figma design using the existing design system.
```

Claude Cowork and Claude cloud sessions do not read personal skills from `~/.claude/skills/`. For those environments, enable the skill for your Claude account or commit it as a project skill when supported by the session.

Claude uses `SKILL.md` and the referenced supporting files. `agents/openai.yaml` contains optional OpenAI/Codex display metadata and is not required by Claude.

See Anthropic's [official Claude Code skills documentation](https://code.claude.com/docs/en/skills) for current installation scopes and invocation behavior.

## Use the skill

Mention the skill explicitly in your Codex prompt:

```text
$dti-design-frontend

Implement the linked Figma design in this repository.

Change: Update the account settings header and action buttons.
Design reference: <Figma frame URL or screenshot>
States: Default, loading, and error.
Screen sizes: Desktop and mobile.
Constraints: Reuse the existing design system. Do not change API behavior.
Verification: Run the relevant checks and preview the affected states.
```

You can also describe a matching frontend task normally. Codex may select the skill automatically based on its description.

Include these details when they matter:

- The exact UI change
- A Figma frame, screenshot, or acceptance criteria
- Relevant states and screen sizes
- What should not change
- Any known product or design-system constraints

## Set up a new product

Each product can document its local commands, design-system paths, patterns, and ownership boundaries in `docs/dti-design-frontend.md`.

Ask Codex:

```text
$dti-design-frontend Prepare this product repository to use the skill. Create docs/dti-design-frontend.md using the included product profile template.
```

The template is available at [`references/product-profile-template.md`](references/product-profile-template.md).

## Human responsibilities

- The designer reviews the diff and decides whether the implementation is visually correct.
- The designer decides when to involve a TPM or engineer.
- The AI agent can identify risks and suggest a question to raise, but it does not contact teammates unless explicitly asked and authorized.
- The AI agent does not commit, push, open a pull request, merge, or deploy unless explicitly asked.

## Repository contents

```text
SKILL.md                                  Skill instructions
agents/openai.yaml                        Optional OpenAI/Codex display metadata
references/product-profile-template.md    Optional per-product setup template
```

For the underlying skill format and supported installation locations, see the [official OpenAI skill documentation](https://developers.openai.com/codex/skills).
