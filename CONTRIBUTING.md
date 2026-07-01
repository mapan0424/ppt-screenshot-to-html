# Contributing

Thanks for helping improve this skill.

## Project Shape

The installable skill lives in `skill/`. Keep the skill itself lean:

- Put agent instructions in `skill/SKILL.md`.
- Put detailed guidance in `skill/references/`.
- Put reusable output assets or templates in `skill/assets/`.
- Put UI metadata in `skill/agents/openai.yaml`.

Repository-level files such as this guide, `README.md`, and `PRIVACY.md` are for open-source maintainers and should not be copied into the installable skill unless there is a specific reason.

## Contribution Guidelines

- Keep instructions concise and procedural.
- Preserve the fixed 1600 x 900 canvas assumption.
- Do not weaken the rule that target screenshots are visual references only.
- Do not add real company, customer, or personal material.
- Prefer synthetic examples with fictional branding and neutral content.
- Avoid adding scripts unless they remove repeated manual work or make validation more reliable.

## Before Opening A Pull Request

Check:

- No private screenshots, deck files, logos, or customer examples are included.
- No emails, names, internal paths, tokens, keys, or private URLs are present.
- `skill/SKILL.md` still has only `name` and `description` in frontmatter.
- `skill/agents/openai.yaml` still matches the skill's purpose.
- The slide template still renders without network access.

Suggested local scan:

```bash
rg -n --hidden -S "(@|https?://|/Users/|token|api[_-]?key|password|secret|confidential|internal|客户|公司|机密)" .
```

Review any matches manually before publishing.
