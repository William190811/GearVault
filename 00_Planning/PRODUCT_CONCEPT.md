# Product Concept — GearVault

## Problem / Solution Summary

**Problem:** Loose peripherals (earbuds, USB drives, small cables, dongles)
carried inside a backpack alongside textbooks and laptops get scratched,
crushed, tangled, or lost because they have no dedicated storage.

**Solution:** GearVault is a small hard-shell "vault" pod that lives inside
the backpack. It is a snap-lid clamshell with fitted internal slots for each
type of item, so peripherals are protected from hard contact and kept
organized in a fixed, findable layout — no zippers, no loose pouch, no
tangling.

## Unique Feature: Integrated Center Cable-Wrap Post

Molded directly into the base as a single raised post, the cable-wrap post
lets a user coil a charging cable or earbud cord around it instead of
letting the cord float loose and tangle with everything else in the vault.
It is part of the base print itself (no separate piece, no added part), so
it costs nothing extra in assembly or material and cannot be lost. This is
the signature differentiator of GearVault versus a generic compartment box —
most small organizer cases only solve "a slot for this item," while
GearVault also solves "and don't let the cable turn into a knot."

## Secondary Feature: Print-in-Place Snap-Pin Hinge

The lid and base are connected by a hinge that prints fully assembled in
place — no hardware (no pins, no screws) and no glue. The hinge uses
interlocking snap lugs sized with a tested clearance so the lid snaps onto
the base pins during printing and then rotates freely. This keeps assembly
to a single snap-fit step per unit and removes an entire category of
manufacturing risk (missing/lost hardware, glue failures, alignment during
bonding).

## Size Variants

Both variants share the same parametric design (same wall thickness, same
hinge and cable-post geometry, scaled and re-populated per size) so both are
produced from one Fusion 360 model with dimension/feature parameters swapped.

| Spec | GearVault Mini | GearVault Pro |
|---|---|---|
| Dimensions (mm) | 70 x 55 x 32 | 80 x 80 x 38 |
| Earbud pocket | 1 | 1 |
| USB slots | 2 | 4 |
| Cable-wrap post | Yes | Yes |
| SD / dongle tray | — | 1 |
| Hinge | Print-in-place snap-pin | Print-in-place snap-pin |
| Assembly | Snap-fit, no hardware/glue | Snap-fit, no hardware/glue |
| Print time/unit | ~2.5 hr | ~4 hr |
| Material/unit | ~22 g PLA | ~38 g PLA |

## Concept Sketch

```
   CLOSED (top view)              OPEN (top view, lid folded back)
   ┌───────────────────┐          ┌───────────────────┐   ┌───────────────┐
   │   G E A R V A U L T│          │   [USB] [USB]      │   │   (lid,       │
   │      (lid, snap    │  hinge→ │   [earbud pocket]  │   │  flat inside, │
   │      ridge border) │          │      ( ● cable-    │   │  no ribs)     │
   └───────────────────┘          │        wrap post)  │   └───────────────┘
                                   └───────────────────┘
        SIDE VIEW (closed)                 CROSS-SECTION
   ┌───────────────────┐            ┌───────────────────┐
   │▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔│ lid (2mm shell)   │  cable post ⬤     │
   │                   │            │  USB slot |‾‾|     │
   │   base (2mm wall) │            │  earbud pocket ◡   │
   └───────────────────┘            └───────────────────┘
```
