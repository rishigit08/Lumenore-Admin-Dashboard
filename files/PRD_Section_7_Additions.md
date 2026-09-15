# PRD — Section 7 Additions (Open Decisions)

## D-02 — Netlink Ceiling Model
**Decision needed:** How is the org-level "ceiling" that bounds sub-license limits defined and where is it set?

**Conclusion (resolved):**
The ceiling is not a separate abstract number. It is the set of org-level feature limit values configured by Netlink Master during org creation, in the **Org Features & Limits** step of the org setup wizard (step 1 of 2). Each feature/module row in that accordion may carry:
- A toggle (enable/disable the feature for the org), and
- Where applicable, an inline numeric limit input (e.g., max dashboards, max shares) tied to that feature.

If a feature is toggled off, it is fully unavailable to the org and any associated limit is not applicable (not enforced, not relevant).

Sub-licenses — created in step 2 (**Licenses**) of the same wizard — are subsets of this ceiling. A sub-license's limit values for any given feature must fall within (at or below) the org-level ceiling value set in step 1 for that same feature. At least one sub-license must be created before users can be onboarded into the org.

**Status:** Closed — reflected in org creation wizard steps 1–2 (see IA update below).

---

## D-03 — Ceiling Enforcement at Sub-License Creation
**Decision needed:** Is the "sub-license must stay within ceiling" rule enforced by the UI, or left to admin discretion?

**Options:**
1. **Hard validation** — sub-license limit input rejects/errors on any value exceeding the corresponding org ceiling value.
2. **Auto-clamp** — input silently caps at the ceiling value if a higher number is entered.
3. **No enforcement** — convention only, no guardrail; relies on Netlink Master judgment.

**Recommendation:** Option 1 (hard validation), consistent with the project's existing pattern of requiring explicit confirmation/guardrails on consequential, data-integrity-sensitive actions (e.g., unassign confirmations, no-silent-default rules for Role/Sub-License at onboarding). A sub-license created above ceiling without a guardrail is a data-integrity bug in the same family as BUG-01 through BUG-06.

**Status:** Open — needs confirmation with dev team before implementation.

---

## D-04 — Category Badge Count Definition
**Decision needed:** For each feature category in the Org Features & Limits accordion, does the numeric badge (e.g., "19") count *feature rows*, or *configurable fields* (toggle + limit input counted separately when both exist on one row)?

**Status:** Open — needs confirmation with dev team. Affects whether a category with, say, 15 toggle-only rows and 4 toggle+limit rows displays "19" or a higher number reflecting the extra limit fields.
