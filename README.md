# DTI Design Frontend

An Agent Skill that helps designers make focused frontend changes in an existing product.

It guides the AI to:

- Find the right code
- Reuse the product's components and design tokens
- Keep changes small and focused
- Run the product's existing checks
- Prepare the result for human review

Use it for layout, typography, responsive behavior, component states, and small interactions. It is not intended for backend or major architecture changes.

## Install

### Codex

Ask Codex to install the skill:

```text
$skill-installer Install https://github.com/zw757/dti-design-frontend
```

For one product only, place the skill at:

```text
<product-repository>/.agents/skills/dti-design-frontend/
```

Restart Codex if the skill does not appear.

### Claude Code

Install it for all your local projects:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/zw757/dti-design-frontend ~/.claude/skills/dti-design-frontend
```

For one product only, place the skill at:

```text
<product-repository>/.claude/skills/dti-design-frontend/
```

Claude Cowork and cloud sessions do not read `~/.claude/skills/`. Enable the skill in your Claude account or add it to the product repository instead.

## Use it

Start your prompt with `$dti-design-frontend` in Codex or `/dti-design-frontend` in Claude Code.

Then describe the change:

```text
Implement this design: <Figma link or screenshot>

Change: Update the account settings header and buttons.
States and sizes: Default, loading, error, desktop, and mobile.
Do not change: API behavior.
Use: Existing design-system components and tokens.
```

The AI may also select the skill automatically when your request matches it.

## Set up a product

A product can store its commands, design-system paths, and working conventions in `docs/dti-design-frontend.md`.

Ask the AI:

```text
Use the DTI Design Frontend skill to create docs/dti-design-frontend.md from the included product profile template.
```

Template: [`references/product-profile-template.md`](references/product-profile-template.md)

## What the designer owns

- Review the visual result and the diff
- Decide when to involve a TPM or engineer
- Explicitly approve any commit, push, pull request, merge, or deployment

The AI can flag risks and suggest questions, but it will not contact teammates or ship changes unless asked.

## Learn more

- [OpenAI skill documentation](https://developers.openai.com/codex/skills)
- [Claude Code skill documentation](https://code.claude.com/docs/en/skills)
