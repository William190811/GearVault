# GearVault Pro — Design Spec (as-built V1)

Built in Fusion 360 as `GearVault_Pro` (Default Project). This spec reflects the actual V1 prototype — see `DESIGN_SPEC_Mini.md` for the design-simplification rationale (friction-fit slip lid instead of a print-in-place hinge).

## 1. Overview

GearVault Pro is the larger variant — same construction as Mini (open-top base tray + friction-fit slip lid), scaled up with an extra divider for a third compartment.

Two bodies, modeled as separate solids in the same Fusion document:
- **Base** — open-top tray with two dividers (3 compartments) and a cable-wrap post
- **Lid** — open-bottom cap that slides down over the base's outside

## 2. Overall Envelope

| Dimension | Value |
|---|---|
| Base outer (L x W x H) | 75 x 75 x 30 mm |
| Lid outer (L x W x H) | 78.8 x 78.8 x 13.6 mm (slides over the base's outside) |
| **Assembled (lid on) footprint** | **78.8 x 78.8 x 30 mm** |
| Assignment max allowed | 80 x 80 x 80 mm |

**Important sizing note:** because the lid telescopes over the *outside* of the base, the assembled footprint is the *lid's* size, not the base's. The base was deliberately sized at 75mm (not 80mm) so the assembled unit — lid included — lands at 78.8mm, safely under the 80mm cap. (An earlier draft of this spec sized the base at the full 80mm cap and would have put the assembled unit at 83.8mm, over the limit — caught and fixed during the Fusion build.)

## 3. Wall / Fillet Rules (both bodies — same as Mini)

| Feature | Value |
|---|---|
| Wall + floor/ceiling thickness | 1.6 mm (uniform) |
| External vertical-edge fillets | 2.0 mm radius |
| Divider wall thickness | 1.6 mm |

## 4. Base Body — Compartment Layout

Base is a single open-top shell, split by **two dividers** into three compartments (all open bins — see Mini's spec for why V1 skips precise item-specific slots):

- **Zone A (40% of interior, ~28mm)** — earbuds, cables; holds the cable-wrap post.
- **Zone B (30% of interior, ~21mm)** — USB drives.
- **Zone C (30% of interior, ~21mm)** — SD cards / small dongles.

### 4.1 Cable-Wrap Post (unique feature)
- Diameter: **10 mm**, Height: **26 mm** (base is 30mm tall — leaves 4mm clearance below the closed lid).
- Positioned in the center of Zone A. Same print-in-place solid cylinder as Mini.

## 5. Lid Body

- Open-bottom shell, skirt height 12mm + 1.6mm cap = 13.6mm total lid height.
- Clearance: 0.3mm per side (same as Mini) for a snug friction fit.
- No latch, no hinge, no hardware.

## 6. Print Settings (recommended)

| Setting | Value |
|---|---|
| Printer | Generic FDM |
| Material | PLA |
| Nozzle | 0.4 mm |
| Layer height | 0.2 mm |
| Infill | 15% |
| Supports | None required |
| Orientation | Base: floor-down. Lid: cap-down (open side up). |

Pro's larger footprint (75x75mm base) is closer to typical bed-adhesion limits for a tall thin-walled part — a brim (2–3mm) is recommended on both bodies.

## 7. Estimated Print Time & Material

| | Value |
|---|---|
| Print time (base + lid combined) | ~4 hours |
| Material weight (base + lid combined) | ~38 g PLA |

## 8. Fusion File

Saved as **`GearVault_Pro`** in the Fusion "Default Project". Reference renders: [02_Product_Render/GearVault_Pro_iso.png](../02_Product_Render/GearVault_Pro_iso.png).
