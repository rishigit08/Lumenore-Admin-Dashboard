# IA Update — Org Creation Wizard (Netlink Master Panel)

Replaces the single "Set Defaults" bullet previously under **1.1.2 Create Organization**.
Also supersedes the earlier draft of **1.6 License Management** where it implied assignment/consumption tracking — License Management is now creation-only (see note at bottom).

```
1.1.2 Create Organization
├── Org Details (name, industry, contact info)
├── Assign Initial Org Admin
├── Set Trial vs Paid
├── Step 1 — Org Features & Limits
│   ├── Accordion, per category (10 categories, plan-tier defaults pre-checked where applicable)
│   ├── Sticky global search
│   ├── Per-feature row:
│   │   ├── Toggle (enable/disable for org) — unchecked = feature fully unavailable, limit not applicable
│   │   └── Inline limit input box (only on rows where the feature has a configurable limit)
│   ├── Category badge count = configurable fields (toggles + limit inputs), not just row count
│   │   — pending D-04 confirmation with dev team
│   └── This step's limit values ARE the org's Netlink ceiling (see D-02, PRD Section 7)
└── Step 2 — Licenses
    ├── Create at least one Sub-License (required before users can be onboarded)
    ├── Sub-license limit values must fall within the Step 1 ceiling per feature
    │   — pending D-03: hard validation vs. auto-clamp vs. no enforcement
    └── (Additional sub-licenses can be created later via 1.6 License Management)
```

## Downstream note — 1.6 License Management (Netlink Master Panel)

Per your latest scoping, License Management is **creation-only**:

```
1.6 License Management
└── Sub-License List
    └── Create Sub-License (values bounded by the org's ceiling, per D-02)
```

Consumption View, AI Credit Pool, and Threshold Alerts do **not** live here — placement for those still needs to be decided (candidates discussed: Usage Analytics, User Detail, or a dedicated Limits & Consumption nav item). This remains open.

## Decisions this closes / opens
- **Closes:** D-02 Netlink ceiling model (PRD Section 7) — ceiling = Step 1 values, sub-licenses are subsets.
- **Opens:** D-03 (ceiling enforcement mechanism), D-04 (category badge count definition) — both logged in `PRD_Section_7_Additions.md`.
