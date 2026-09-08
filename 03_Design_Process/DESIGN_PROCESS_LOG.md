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

## 2a. v1.1 — Rebuild: separate designs, real earbud-case fit, engraved logo

The v1 models above were lost when Fusion's cloud save silently failed (no active license at the time — `Document.saveAs()` returned `True` but never actually uploaded). Rebuilt from scratch once a Fusion personal-use license was activated, with three requested changes plus a compartment redesign:

| Field | Notes |
|---|---|
| Date | 2026-09-08 |
| Author | William (+ Claude Code, via Fusion 360 MCP) |
| Fusion 360 file / version | `GearVault_Mini`, `GearVault_Pro` — **two fully separate Fusion documents** (not configurations of one design), each properly cloud-saved this time (`isSaved=True` confirmed) |
| Change 1: separate designs | Confirmed each variant lives in its own document/save, addressing the earlier ambiguity. |
| Change 2: earbud-case fit | Original v1 earbud zone was sized arbitrarily (never checked against a real case). Redesigned the compartment layout: divider now runs parallel to the long axis so the case bay gets the full 65.8mm length, sized to a real case envelope (up to ~61x48x27mm — AirPods, AirPods Pro, Galaxy Buds-family). Cable-wrap post moved into its own adjacent lane so it can't block the case. |
| Change 3: engraved logo | "GearVault" engraved 0.4mm deep into the lid top, ~5mm tall, centered. |
| Bugs caught and fixed during this rebuild | (1) **Wrong face opened on the lid** — face-matching by `Plane.origin.z` alone falsely matched a vertical side face (its origin also reported z≈0), so the shell operation opened a side wall and left the bottom sealed shut. Fixed by also checking the face normal is horizontal before matching. Caught by volume math (18.8cm³ actual vs ~12.4cm³ expected for a correctly open-bottom shell) — visual screenshots alone didn't catch it. (2) **Engraving cut removed the wrong material twice**: first attempt cut in the wrong direction (extruded away from the material, a no-op); second attempt used the sketch's whole-face boundary profile instead of the letter shapes (text needs `SketchText.explode()` before it produces real letter profiles), which lowered the *entire* top face by 0.4mm instead of just the letters. Fixed by exploding the text and filtering `sketch.profiles` to only the letter-sized ones, plus using a negative extrude distance to cut inward. Verified by checking horizontal face groups by z-height before trusting a screenshot. |
| Exports | Native `.f3d` archived to `01_Fusion360_Design/CAD_Source/`, print-ready `.stl` per body to `01_Fusion360_Design/STL/` — local exports also failed silently without a license (STEP returned `False`, STL threw an internal error) until the personal-use license was activated. |

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
