# canada-tax

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill for preparing and filing Canadian personal income taxes (T1).

## Coverage

- **Federal:** Complete — all income lines, deductions, credits, and refundable credits (2024 & 2025)
- **Ontario:** Complete — ON428, ON479, ON-BEN, Ontario Health Premium, surtax, LIFT, OTB, OEPTC
- **Other provinces:** Not yet covered. Contributions welcome — see [Adding a Province](#adding-a-province).

## Installation

Copy or symlink into your project's `.claude/skills/` directory:

```bash
# Clone
git clone https://github.com/aelfalou/canada-tax-skill.git

# Symlink into your project
mkdir -p /path/to/your/project/.claude/skills
ln -s /path/to/canada-tax-skill /path/to/your/project/.claude/skills/canada-tax
```

Then use `/canada-tax` in Claude Code, or it will trigger automatically when you discuss Canadian tax topics.

## Structure

```
canada-tax-skill/
├── SKILL.md                          # Main guide (federal + workflow)
└── references/
    ├── federal-details.md            # Brackets, all income/deduction lines, credit amounts
    ├── forms-checklist.md            # Every federal + Ontario form with decision tree
    └── ontario-tax-details.md        # ON428, ON479, ON-BEN, surtax, OHP, marginal rates
```

## Adding a Province

To add support for another province:

1. Create `references/<province>.md` (e.g., `british-columbia.md`) covering:
   - Provincial tax brackets
   - Provincial non-refundable credits and amounts
   - Provincial refundable credits
   - Provincial benefit applications (equivalent of ON-BEN)
   - Any province-specific forms and schedules
2. Update `SKILL.md` to route to the correct reference file based on province of residence
3. Update `references/forms-checklist.md` with the province's forms

Quebec requires special handling — it has a completely separate return (TP-1) filed with Revenu Québec.

## Disclaimer

This skill is based on the 2024 and 2025 tax packages from canada.ca/cra. It is not professional tax advice. Always verify amounts against your Notice of Assessment and CRA My Account.
