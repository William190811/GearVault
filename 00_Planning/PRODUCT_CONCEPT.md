# Product Concept — GearVault

## Problem / Solution Summary

**Problem:** Loose peripherals (earbuds, USB drives, small cables, dongles)
carried inside a backpack alongside textbooks and laptops get scratched,
crushed, tangled, or lost because they have no dedicated storage.

**Solution:** GearVault is a small hard-shell "vault" pod that lives inside
the backpack. It's an open-top base tray with a friction-fit slip-on lid,
so peripherals are protected from hard contact and kept organized in a
fixed layout — no zippers, no loose pouch, no tangling.

## Unique Feature: Integrated Center Cable-Wrap Post

Molded directly into the base as a single raised post, the cable-wrap post
lets a user coil a charging cable or earbud cord around it instead of
letting the cord float loose and tangle with everything else in the vault.
It is part of the base print itself (no separate piece, no added part), so
it costs nothing extra in assembly or material and cannot be lost. This is
the signature differentiator of GearVault versus a generic compartment box —
most small organizer cases only solve "a slot for this item," while
GearVault also solves "and don't let the cable turn into a knot."

## Closure: Friction-Fit Slip-On Lid *(revised from the original hinge concept)*

The first concept used a print-in-place snap-pin hinge. During Fusion 360
modeling we deliberately simplified this to a **friction-fit slip-on lid**
that fully lifts off, like a small pencil case: the lid is an open-bottom
cap that slides down over the outside of the base and grips by friction
(0.3mm clearance per side) — no hinge, no latch, no hardware, no glue.

A hinge is the single highest-risk feature to get right on a first print
(tight lug/socket tolerances, real chance of a cracked or seized joint),
and it doesn't add anything to what the product needs to do. The slip lid
has exactly one clearance value to tune instead of several, removes an
entire category of print-failure risk, and still fully closes and protects
the contents. See `03_Design_Process/DESIGN_PROCESS_LOG.md` for the full
reasoning.

## Size Variants (V1.1 — earbud-case-fit revision)

Both variants share the same construction (open-top base tray + slip-on
lid, cable-wrap post, rounded edges, engraved "GearVault" wordmark on the
lid) but are built and saved as **two entirely separate Fusion 360
documents** (`GearVault_Mini`, `GearVault_Pro`), not two configurations of
one design.

The earbud-case bay is sized to a real charging-case envelope (up to
~61 x 48 x 27mm — covers AirPods, AirPods Pro, and most Galaxy Buds-style
cases with margin), and both variants share the identical case-bay
footprint so the fit is consistent across sizes.

| Spec | GearVault Mini | GearVault Pro |
|---|---|---|
| Base outer (mm) | 69 x 65 x 29 | 69 x 75 x 30 |
| **Assembled (lid on) footprint (mm)** | 72.8 x 68.8 x 29 | 72.8 x 78.8 x 30 |
| Case bay (clear, mm) | 65.8 x 50.0 | 65.8 x 50.0 |
| Second compartment | Cable lane (10.2mm) — cable-wrap post only | Accessory lane (20.2mm) — USB drives, SD/dongles, cable-wrap post |
| Cable-wrap post | 8mm dia, 22mm tall | 10mm dia, 24mm tall |
| Engraved logo | Yes ("GearVault" on lid) | Yes ("GearVault" on lid) |
| Closure | Friction-fit slip-on lid | Friction-fit slip-on lid |
| Assembly | None — lid lifts fully off | None — lid lifts fully off |
| Print time/unit | ~2.5 hr | ~4 hr |
| Material/unit | ~22 g PLA | ~38 g PLA |

Note: the assignment's 80x80x80mm cap applies to the *assembled* unit —
since the lid telescopes over the base's outside, the assembled footprint
is the lid's size, not the base's. Both variants stay comfortably under cap
(see `01_Fusion360_Design/DESIGN_SPEC_Pro.md` for the sizing math).

## Concept Sketch (as-built)

```
   CLOSED (top view)              OPEN (lid lifted off)
   ┌───────────────────┐          ┌──────────────┬────┐   ┌───────────────┐
   │   G E A R V A U L T│          │              │ ●  │   │   (lid,       │
   │   (lid slips over  │  lift → │  earbud case │cable│   │   friction-   │
   │    base, no hinge) │          │     bay      │lane│   │   fit skirt,  │
   └───────────────────┘          └──────────────┴────┘   │   engraved)   │
                                     ● = cable-wrap post    └───────────────┘
        SIDE VIEW (closed)                 CROSS-SECTION
   ┌───────────────────┐            ┌───────────────────┐
   │▔▔"GearVault"▔▔▔▔▔▔│ lid (engraved top)   │  case bay (deep)   │
   │                   │            │  |  cable post ⬤   │
   │   base (open top) │            │  |  lane            │
   └───────────────────┘            └───────────────────┘
```

Reference renders (Fusion viewport captures of the actual model):
[02_Product_Render/GearVault_Mini_iso.png](../02_Product_Render/GearVault_Mini_iso.png),
[02_Product_Render/GearVault_Pro_iso.png](../02_Product_Render/GearVault_Pro_iso.png).
