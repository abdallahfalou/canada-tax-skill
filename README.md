# canada-tax

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill that walks you through preparing and filing your Canadian personal income tax return (T1). It knows every federal and provincial form, credit, deduction, and benefit — so you don't have to.

## What It Does

When you invoke this skill, Claude becomes a tax assistant that:

1. Asks about your situation (income, marital status, dependants, province)
2. Identifies every form and schedule you need
3. Walks through each deduction and credit you may qualify for
4. Flags missing documents and tells you where to get them
5. Optimizes your return (which spouse claims medical, donation carryforward, RRSP timing)

It covers both the federal T1 return and provincial forms, with reference tables for tax brackets, credit amounts, and line-by-line details.

## Provincial Coverage

| Province | Status |
|---|---|
| Ontario | Complete — ON428, ON479, ON-BEN, OHP, surtax, LIFT, OTB, OEPTC |
| Other provinces | Not yet covered — [contributions welcome](#adding-a-province) |

The federal portion (~70% of the skill) applies to all provinces. Quebec requires special handling as it has a completely separate return (TP-1) filed with Revenu Quebec.

## Installation

### Option 1: As a Plugin (Recommended)

```bash
# From Claude Code, add the marketplace and install:
/plugin marketplace add abdallahfalou/canada-tax-skill
/plugin install canada-tax
```

### Option 2: Personal Skill (Available in All Projects)

```bash
git clone https://github.com/abdallahfalou/canada-tax-skill.git ~/repos/canada-tax-skill
mkdir -p ~/.claude/skills
ln -s ~/repos/canada-tax-skill ~/.claude/skills/canada-tax
```

### Option 3: Project Skill (This Project Only)

```bash
git clone https://github.com/abdallahfalou/canada-tax-skill.git ~/repos/canada-tax-skill
mkdir -p .claude/skills
ln -s ~/repos/canada-tax-skill .claude/skills/canada-tax
```

After installing, the skill is available as `/canada-tax` in Claude Code. It also triggers automatically when you discuss Canadian tax topics.

## Usage

### Getting Started

The easiest way to start is to gather your tax documents into a folder, then invoke the skill:

```
/canada-tax
```

Claude will ask about your situation and guide you through the return step by step.

### Recommended Folder Setup

Before starting, dump your tax documents into a working folder. Loose organization is fine — Claude will sort through them:

```
Tax 2024/
├── T4_slip.pdf
├── T5_slip.pdf
├── T2200_home_office.pdf
├── donation_receipts/
│   ├── charity_a_receipt.pdf
│   ├── charity_b_receipt.pdf
│   └── launchgood_donations.csv
├── medical/
│   ├── dental_receipt.pdf
│   └── pharmacy_receipts.pdf
├── home_office/
│   ├── hydro_bills/
│   ├── internet_bills/
│   └── utility_bills/
├── property_tax_statement.pdf
└── CRA_notice_of_assessment.pdf
```

Then point Claude at the folder and let it work:

```
I'm filing my 2024 taxes. All my documents are in Tax 2024/. Let's go.
```

### Example Session

Here's what a typical session looks like (fictional taxpayer):

> `/canada-tax`

I'll help you prepare your 2024 T1 return. Let me start with your profile:

- What province did you live in on Dec 31, 2024?
- What's your marital status?
- Any dependants (children under 18, elderly parents, disabled relatives)?
- Did you have any major life changes in 2024 (new home, marriage, new job, move)?

> Ontario. Married, no kids. Bought our first home in June. No other changes. My documents are in the Tax 2024/ folder.

Congrats on the home! That opens up some credits. Let me review your documents...

*reads T4, T5, donation receipts, utility bills*

Based on your T4 and documents, here's what I've found:

**Income:**
- Employment income: $85,000 (T4)
- Interest income: $342 (T5)

**Deductions & credits you qualify for:**
- Basic personal amount ($15,705)
- Canada employment amount ($1,433)
- CPP/EI contributions (from T4)
- Home buyers' amount ($10,000) — since you bought your first home
- Charitable donations ($2,450 across 3 charities)
- Medical expenses ($1,200 dental + $480 prescriptions)

**Documents I still need:**
- Property tax statement (for ON-BEN / Ontario Trillium Benefit)
- T2200 from your employer if you worked from home
- Your spouse's net income (affects some credits)
- CRA Notice of Assessment (for RRSP room)

> Property tax was $3,200. I do work from home — T2200 is in the folder. Spouse made about $52,000.

Got it. Let me calculate your home office deduction...

*reads T2200, utility bills, calculates office percentage*

Your office is 120 sq ft of 1,100 sq ft = 10.9%. Based on your utility bills:
- Hydro: $1,440/year x 10.9% = $156.96
- Internet: $960/year x 10.9% = $104.64
- Water/utilities: $1,800/year x 10.9% = $196.20
- **Total home office deduction: $457.80**

For ON-BEN, I'll enter your $3,200 property tax to apply for the Ontario Energy and Property Tax Credit.

Your spouse's income of $52,000 is too high for the spouse amount, but medical expenses should be claimed by whichever of you has the lower net income for a larger credit.

Should I draft your complete filing plan with all the numbers?

### What the Skill Covers

The skill follows an 11-step workflow:

| Step | What Happens |
|---|---|
| 1 | Gather taxpayer profile (province, marital status, dependants) |
| 2 | Identify all income sources and match to tax slips |
| 3 | Check every applicable deduction (RRSP, home office, child care, etc.) |
| 4 | Walk through federal non-refundable credits |
| 5 | Check federal tax calculation credits and refundable credits |
| 6 | Calculate Ontario tax (ON428) |
| 7 | Check Ontario refundable credits (ON479) |
| 8 | Apply for Ontario Trillium Benefit (ON-BEN) |
| 9 | Identify benefits triggered automatically by filing |
| 10 | Generate forms checklist |
| 11 | Confirm filing deadlines |

## File Structure

```
canada-tax-skill/
├── SKILL.md                          # Main guide — workflow + federal content
└── references/
    ├── federal-details.md            # Tax brackets, all income/deduction lines, credit amounts
    ├── forms-checklist.md            # Every federal + Ontario form with decision tree
    └── ontario-tax-details.md        # ON428, ON479, ON-BEN, surtax, OHP, marginal rates
```

Claude loads SKILL.md into context when the skill triggers, then reads the relevant reference files on demand (e.g., only loading Ontario details for Ontario residents).

## Adding a Province

To add support for another province:

1. Create `references/<province>.md` (e.g., `british-columbia.md`) covering:
   - Provincial tax brackets and rates
   - Provincial non-refundable credits and amounts
   - Provincial refundable credits
   - Provincial benefit applications (equivalent of ON-BEN)
   - Any province-specific forms and schedules
2. Update `SKILL.md` to route to the correct reference file based on province of residence
3. Update `references/forms-checklist.md` with the province's forms

Use `references/ontario-tax-details.md` as a template for the expected structure and level of detail.

## Disclaimer

This skill is based on the 2024 and 2025 tax packages from [canada.ca/cra](https://www.canada.ca/en/revenue-agency.html). It is not professional tax advice. Always verify amounts against your Notice of Assessment and CRA My Account, and consult a tax professional for complex situations.
