# Release Checklist

Use this checklist before publishing the repository.

## Required

- [ ] Confirm all example assets are synthetic or redistributable.
- [ ] Confirm no real company, customer, or personal information is present.
- [ ] Confirm no real PPT, PPTX, PDF, ZIP, or exported customer slide image is committed.
- [ ] Confirm no generated HTML output contains private wording from a real deck.
- [ ] Run the sensitive text scan from `CONTRIBUTING.md`.
- [ ] Manually inspect all images, HTML files, and screenshots.
- [ ] Validate the installable skill folder.
- [ ] Review `README.md`, `PRIVACY.md`, and `LICENSE`.

## Skill Validation

If you have access to the Codex skill creator validation script, run:

```bash
python3 path/to/skill-creator/scripts/quick_validate.py skill
```

The expected result is:

```text
Skill is valid!
```

## Suggested First Release

Tag the first public release as `v0.1.0`.

Describe it as an initial public release containing:

- Codex skill instructions;
- fixed 1600 x 900 HTML slide template;
- high-fidelity reconstruction guide;
- privacy and contribution guidelines.
