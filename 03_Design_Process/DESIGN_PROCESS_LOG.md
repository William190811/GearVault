# GearVault Design Process Log

Tracks the real design iteration history for GearVault Mini and Pro, from first concept through final design lock. Sections 3–6 (prototype prints) are still templates — fill in with real print/test-fit data once physical units come off the printer.

Reference specs: `01_Fusion360_Design/DESIGN_SPEC_Mini.md`, `01_Fusion360_Design/DESIGN_SPEC_Pro.md`

---

## 1. v0 — Concept Sketch

| Field | Notes |
|---|---|
| Date | 2026-09-08 |
| Author | William (+ Claude Code) |
| Sketch/reference file | `00_Planning/PRODUCT_CONCEPT.md` (ASCII concept sketch) |
| Concept summary | Clamshell pod, print-in-place snap-pin hinge, earbud pocket + USB slots + cable-wrap post in base |
| Key open questions at this stage | Hinge tolerance (lug/socket clearance) was untested and identified as the highest-risk feature for a first print |

---

## 2. v1 — First Fusion 360 Model (built, not yet printed)

| Field | Notes |
|---|---|
| Date | 2026-09-08 |
| Author | William (+ Claude Code, via Fusion 360 MCP) |
| Fusion 360 file / version | `GearVault_Mini`, `GearVault_Pro` (Default Project) |
| What was modeled | Both bodies for each size: **Base** (open-top tray, divider wall(s), cable-wrap post) and **Lid** (open-bottom friction-fit slip cap). Rounded outer edges (2mm fillet) on both bodies. |
| Deviations from spec at this point | **Design simplification, made deliberately during modeling, not a mistake:** dropped the print-in-place snap-pin hinge + snap-ridge latch entirely in favor of a friction-fit slip-on lid. Rationale: a hinge is the single highest-risk feature to get right on a first print (tight lug/socket tolerance, real chance of a cracked or seized joint), and the brief explicitly favors a high-confidence, not-over-engineered V1. A slip lid has one clearance value (0.3mm/side) instead of several, and still fully closes and protects the contents. Also dropped precise per-item USB slots in favor of simple open bins — sizing slots to a "standard" USB stick without having tested against real hardware was a guess; open bins are protected and organized without that risk, and V2 can tighten the fit using real feedback. |
| Bug caught during modeling | Pro's base was initially sized at the full 80mm cap. Since the lid telescopes *over* the base's outside, the assembled (lid-on) footprint is the lid's size, not the base's — that would have put the real assembled unit at 83.8mm, over the assignment's 80mm limit. Caught by checking bounding boxes in Fusion before saving; fixed by shrinking Pro's base to 75mm so the assembled unit lands at 78.8mm. |
| Known risks going into first print | Lid friction-fit clearance (0.3mm/side) is a starting estimate, not yet tested — may need widening if the lid is too tight, or tightening if it falls off. Open-bin compartment sizes are generous by design; real items may want more definition (see V2 improvement doc). |

---

## 3. Prototype Print #1

| Field | Notes |
|---|---|
| Date | |
| Printer / settings used | |
| What was tested | |
| Test-fit results — compartments (Zone A/B/[C]) | |
| Test-fit results — cable-wrap post | |
| Test-fit results — lid friction fit | |
| What worked | |
| What failed | |
| Print time / weight actual vs. estimate | |

*(Fill in once the first physical unit is printed — see `00_Planning/MANUFACTURING_PLAN.md` for the test-print-first batch strategy: 1 Mini + 1 Pro before committing to the remaining 8 units.)*

---

## 4. Dimensional Adjustments Made

Track every measured change to spec values here, with before/after and the reason (usually a prototype test-fit result above).

| Dimension | Original spec value | Adjusted value | Reason | Source (prototype #) |
|---|---|---|---|---|
| | | | | |

---

## 5. Prototype Print #2

| Field | Notes |
|---|---|
| Date | |
| Printer / settings used | |
| Changes carried in from Section 4 | |
| Test-fit results | |
| Remaining issues | |
| Print time / weight actual vs. estimate | |

---

## 6. Final Design Lock

| Field | Notes |
|---|---|
| Date locked | |
| Fusion 360 file / version (final) | |
| Summary of final parameter values (Mini) | |
| Summary of final parameter values (Pro) | |
| Sign-off | |
| Notes for manufacturing run (10 units) | |

---

### Action item

Once the first physical prints exist, fill in Section 3 with real test-fit results (especially the lid's friction-fit clearance and how items actually sit in the open bins), and update `01_Fusion360_Design/DESIGN_SPEC_Mini.md` / `DESIGN_SPEC_Pro.md` with any dimensional changes from Section 4.
