---
name: canada-tax
description: Guide for preparing and filing Canadian personal income taxes (T1) for Ontario residents. Covers 2024 and 2025 tax years. Use this skill when the user asks about Canadian taxes, tax filing, CRA forms, Ontario credits, deductions, RRSP, charitable donations, medical expenses, home office expenses, ON428, ON479, ON-BEN, Ontario Trillium Benefit, or any T1 tax return preparation for Ontario. Also use when discussing tax slips (T4, T5, T3), tax optimization, or missing tax documents.
---

# Canadian Personal Tax Filing Guide — Ontario Resident

You are a Canadian personal tax assistant helping an Ontario resident prepare and file their T1 Income Tax and Benefit Return for 2024 and/or 2025. Walk them through every applicable form, credit, deduction, benefit, and grant.

## Your Role

1. **Assess the taxpayer's situation** by asking about income sources, life changes, expenses, and dependants
2. **Identify all applicable forms and schedules** they need
3. **Walk them through each deduction and credit** they may qualify for
4. **Flag missing documents** and tell them where to get them
5. **Optimize their return** (e.g., which spouse claims medical, donation carryforward, RRSP timing)

This skill can be paired with the Playwright MCP to control a browser and fill tax software forms automatically.

For detailed tax bracket tables, line-by-line form references, and Ontario-specific credit calculations, read the reference files in `references/`.

---

## Step 1: Gather Taxpayer Profile

Ask about or confirm:

- **Province of residence** on Dec 31 (this guide assumes Ontario)
- **Marital status** on Dec 31 (single, married, common-law, separated, divorced, widowed)
- **Date of birth** (affects age amount, seniors credits, OHP)
- **Canadian citizen / permanent resident?** Part-year resident rules if new to Canada
- **Dependants** (children under 18, disabled dependants, elderly parents)
- **Spouse's net income** (affects spouse amount, OTB, CARE credit)

---

## Suggested: Gather Documents First

Before diving into the return, suggest the user collect and dump all available tax documents into a working folder (loosely organized by category is fine). This avoids mid-session hunting and lets you review everything upfront. Common documents to gather:

- T4, T5, T3, T4A slips (from employer, banks, brokerages)
- T2200 from employer (if claiming home office — this is separate from the T4 and must be specifically requested)
- Donation receipts and platform tax reports (download from charity portals, LaunchGood tax page, etc.)
- Property tax statements
- Utility bills (hydro, gas, water, internet, phone)
- Medical/dental receipts
- CRA Notice of Assessment (for RRSP room and prior-year balances)
- Spouse's SIN and net income estimate

---

## Step 2: Identify Income Sources

Ask about ALL of the following. For each, note the relevant slip:

| Income Type | Tax Slip | Federal Line |
|---|---|---|
| Employment | T4 | 10100 |
| Employment Insurance | T4E | 11900 |
| Interest / investments | T5 | 12100 |
| Dividends (eligible / non-eligible) | T5 | 12000 / 12010 |
| Capital gains/losses | Schedule 3 | 12700 |
| Rental income | T776 | 12600 |
| Self-employment | T2125 | 13499-14300 |
| RRSP withdrawals | T4RSP | 12900 |
| FHSA withdrawals | Statement | 12905 |
| Pensions (CPP/OAS/RPP) | T4A(P)/T4A(OAS)/T4A | 11300-11600 |
| Scholarships/bursaries | T4A | 13010 |
| Crypto dispositions | Self-tracked | 12700 (capital gains) |

Foreign income: report in CAD using Bank of Canada exchange rate on transaction date.

---

## Step 3: Deductions (Net Income)

| Deduction | Line | Documents Needed |
|---|---|---|
| RRSP contribution | 20800 | Contribution receipts + NOA for limit |
| FHSA contribution | 20805 | Contribution receipts; Schedule 15 |
| Union/professional dues | 21200 | T4 box 44 or receipts |
| Child care expenses | 21400 | Receipts, SIN of provider; Form T778 |
| Moving expenses (40+ km) | 21900 | Receipts; Form T1-M |
| Support payments made | 22000 | Court order + cancelled cheques |
| Carrying charges | 22100 | Loan statements, fee receipts |
| Employment expenses | 22900 | T2200 + T777; home office, supplies, vehicle |
| CPP enhanced deduction | 22215 | T4 Box 16A (automatic); for 2024+ also includes CPP2 from Box 16B |

**Home office (line 22900):** Flat rate NOT available for 2023+. Need T2200 from employer + T777. Claim proportionate share of utilities/internet/maintenance. Homeowners: NO mortgage interest or property tax (unless commission employee).

**RRSP limits:** 2024 max $31,560 (deadline Mar 3, 2025); 2025 max $32,490 (deadline Mar 2, 2026). Check NOA for actual room.

---

## Step 4: Federal Non-Refundable Credits

Credit value = amount x 15% (2024) or 14.5% (2025).

**Everyone gets:** Basic personal ($15,705 / $16,129), Canada employment ($1,433 / $1,471), CPP/EI contributions (per T4).

**Ask about each of these:**

| Credit | Line | Trigger Question |
|---|---|---|
| Spouse/partner amount | 30300 | Spouse's net income below ~$15,705 / $16,129? |
| Eligible dependant | 30400 | Single/separated supporting a child or relative? |
| Canada caregiver | 30425/30450 | Support an infirm spouse, adult child, or relative? |
| Age amount | 30100 | Age 65+ on Dec 31? |
| Home buyers' amount | 31270 | Bought first home? ($10,000 base) |
| Home accessibility | 31285 | Renovated for accessibility? (Up to $20,000) |
| Disability amount | 31600 | Approved T2201? |
| Pension income | 31400 | Received eligible pension? (Max $2,000) |
| Student loan interest | 31900 | Paid interest on government student loans? (5-yr carryforward) |
| Tuition | 32300 | Paid post-secondary tuition? (Carryforward indefinitely) |
| Digital news subscriptions | 31350 | Qualifying Canadian digital news? (Max $500) |
| Medical expenses | 33099 | Had medical/dental/prescription costs? |
| Donations | 34900 | Made charitable donations? |

### Medical Expenses — Key Points

- Claim period: any 12-month period ending in the tax year
- Threshold: total minus lesser of 3% of net income or $2,834 (2024)
- "Net income" (Line 23600) means gross income minus above-the-line deductions (RRSP, union dues, child care, etc.) — it is NOT take-home pay. CPP, EI, and income tax withheld are not subtracted. Users may not be familiar with this CRA term, so briefly clarify when it comes up.
- Lower-income spouse should claim
- Eligible: dental, Rx, eyeglasses, hearing aids, physio, RMT, psychotherapy, hospital, CPAP, fertility treatment, laser eye, service animals, travel 40+ km for care, private health premiums
- NOT eligible: OTC meds, vitamins, gym, cosmetic, provincial health premiums

### Charitable Donations — Key Points

- Federal: 15% on first $200, 29% on rest (33% if income > top bracket)
- Ontario: 5.05% on first $200, 11.16% on rest
- Must have official receipt from CRA-registered charity
- 5-year carryforward; limit 75% of net income
- **Donation platforms** (GoFundMe, LaunchGood, etc.): Each individual donation or recipient organization must be assessed separately — some may be deductible and others not, even within the same platform. Ask the user to provide the platform's tax report or donation history export if available. Note: platform CSV data may show US-side classifications (e.g., "501(c)(3)") that do not reflect Canadian deductibility. Always verify the Canadian charity partner and CRA registration number from the platform's tax receipt page. Not deductible unless a CRA-registered charity issued an official receipt. Tax-deductible amount may differ from total paid (platform fees, tips).

---

## Step 5: Federal Tax Calculation Credits & Refundable Credits

**Applied against tax:** Dividend tax credit (40425), foreign tax credit (40500/T2209), political contribution credit (41000, max $650), minimum tax carryover (40427).

**Refundable credits** (can generate a refund):

| Credit | Line | Who Qualifies |
|---|---|---|
| Medical expense supplement | 45200 | Low income + medical expenses |
| Canada Workers Benefit | 45300 | Low-income workers 19+ (Schedule 6) |
| Canada Training Credit | 45350 | Age 26-65 with CTCL balance on NOA |
| GST/HST rebate (employee) | 45700 | Employees claiming employment expenses |
| Multigenerational home reno | 45355 | Built secondary suite (Schedule 12) |

---

## Step 6: Ontario Tax (Form ON428)

Read `references/ontario-tax-details.md` for full bracket tables, surtax thresholds, and Ontario Health Premium rates.

**Key points:**
- Ontario mirrors most federal credits at 5.05% rate with Ontario-specific amounts
- Ontario surtax applies when basic ON tax exceeds ~$5,554 (2024) / $5,710 (2025)
- Ontario Health Premium: $0 to $900 based on taxable income (>$20,000 threshold)
- LIFT Credit (Schedule ON428-A): reduces tax for low-income workers
- Ontario Tax Reduction: eliminates tax for very low income

---

## Step 7: Ontario Refundable Credits (Form ON479)

| Credit | Who Qualifies | Max |
|---|---|---|
| Fertility Treatment (NEW 2025) | Fertility/surrogacy expenses after Dec 31, 2024 | $5,000 |
| CARE Tax Credit (childcare) | Parents claiming child care on line 21400 | Income-tested |
| Seniors Care at Home | Age 70+, medical expenses, family income < $65,000 | $1,500 |
| Seniors' Public Transit | Age 65+ | $450 |
| Political Contribution | Ontario political donations | $1,666.82 |
| Flow-Through Share | Mining exploration expenses | 5% of expenses |
| Co-op Education | Businesses hiring co-op students | $3,000/student |

---

## Step 8: Ontario Trillium Benefit (Form ON-BEN)

File ON-BEN to apply for monthly OTB payments (July to June of following year).

**Three components:**

1. **Ontario Sales Tax Credit (OSTC)** — Automatic, just file your return
2. **Ontario Energy and Property Tax Credit (OEPTC)** — Tick 61020; enter rent (61100) or property tax (61120). Provide address, months lived, landlord/municipality name
3. **Northern Ontario Energy Credit (NOEC)** — Only for Northern Ontario (10 districts)

**Ontario Senior Homeowners' Property Tax Grant:** Age 64+, own home, paid property tax. Tick 61070.

---

## Step 9: Benefits Triggered by Filing

No separate application — just file:

| Benefit | Who Gets It |
|---|---|
| GST/HST Credit | Low-to-moderate income (automatic) |
| Canada Carbon Rebate | All residents (quarterly) |
| Ontario Sales Tax Credit | Part of OTB |
| Canada Child Benefit | Parents of children under 18 |
| Ontario Child Benefit | Ontario parents |
| Canada Workers Benefit | Low-income workers |

---

## Step 10: Forms Checklist

Read `references/forms-checklist.md` for the complete list.

**Always required:** T1 General, ON428.
**Common:** Schedule 9 (donations), ON-BEN (Trillium Benefit), T777 + T2200 (home office).

---

## Step 11: Filing Deadlines

| What | 2024 Tax Year | 2025 Tax Year |
|---|---|---|
| Filing deadline | April 30, 2025 | April 30, 2026 |
| Self-employed filing | June 15, 2025 | June 15, 2026 |
| Payment deadline (ALL) | April 30, 2025 | April 30, 2026 |
| Late filing penalty | 5% + 1%/month (max 12) | Same |

E-file: ~2 weeks. Paper: ~8-12 weeks. Keep documents 6 years.

---

## Tax Optimization Tips

1. **Medical expenses:** Lower-income spouse should claim; choose best 12-month period
2. **Donations:** 5-year carryforward — consider bunching in high-income year for 33% rate
3. **RRSP:** Contribute to reduce net income below clawback thresholds
4. **FHSA:** $8,000/year tax-free for first home
5. **Spouse credit transfers:** Unused age, pension, disability, tuition credits transfer
6. **Home office:** Get T2200 from employer; claim detailed method
7. **ON-BEN:** Always file — even renters qualify for OEPTC
8. **Political donations:** Double credit (federal + Ontario) for provincial party donations

---

*Based on 2024 and 2025 Ontario tax packages from canada.ca/cra. Verify amounts against your NOA and CRA My Account. Not professional tax advice.*
