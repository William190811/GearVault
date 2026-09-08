# GearVault Mini — Design Spec (as-built V1)

Built in Fusion 360 as `GearVault_Mini` (Default Project). This spec reflects the actual V1 prototype, not the original hinge concept — see the "Design simplification" note below.

## 1. Overview

GearVault Mini is the smaller of two size variants — a hard-shell tray with a friction-fit slip-on lid for loose backpack peripherals (earbuds, USB drives, cables, dongles).

Two bodies, modeled as separate solids in the same Fusion document:
- **Base** — open-top tray with a center divider and integrated cable-wrap post
- **Lid** — open-bottom cap that slides down over the base's outside, held on by friction

### Design simplification (V1 decision)
The original concept called for a print-in-place snap-pin hinge + separate snap-ridge latch. That geometry is fussy to get right on a first print (tight tolerances, real risk of a cracked socket or a hinge that won't rotate — see the ORIGINAL failure-mode notes that used to live here). For a high-confidence V1, we replaced the hinge with a **fully removable friction-fit slip lid** — zero moving parts, one clearance value to get right (0.3mm per side), and it still fully closes and protects the contents. A living hinge is a reasonable V2 experiment once real print data exists.

## 2. Overall Envelope

| Dimension | Value |
|---|---|
| Base outer (L x W x H) | 70 x 55 x 24 mm |
| Lid outer (L x W x H) | 73.8 x 58.8 x 11.6 mm (slides over the base's outside) |
| Assembled (lid on) footprint | 73.8 x 58.8 x 24 mm |
| Assignment max allowed | 80 x 80 x 80 mm — comfortably under cap on all axes |

The lid nests down over the top portion of the base's wall, so assembled height stays at the base's own height (24mm) — the lid doesn't add height, only wraps around the top ~10mm of the base's outside.

## 3. Wall / Fillet Rules (both bodies)

| Feature | Value |
|---|---|
| Wall + floor/ceiling thickness | 1.6 mm (uniform — simpler and more robust than a separate thinner floor) |
| External vertical-edge fillets | 2.0 mm radius (soft edges — nothing sharp against other bag contents) |
| Divider wall thickness | 1.6 mm |

## 4. Base Body — Compartment Layout

Base is a single open-top shell (floor-down on the print bed, cavity opening straight up — zero overhangs, zero supports) split by **one center divider** into two compartments:

- **Zone A (55% of interior, ~36mm long)** — earbuds, cables; holds the cable-wrap post.
- **Zone B (45% of interior, ~29mm long)** — USB drives / small dongles, loose (not individual friction slots — see rationale below).

### Why open bins instead of precise USB slots
The original spec cut individual friction-fit slots sized to a "standard" USB stick (+0.4mm clearance). That's a guess until we've tested against real hardware, and a wrong guess means a wasted print. V1 uses simple open bins sized generously enough to hold multiple small items loosely but protected by the walls — real fit feedback from the 10-unit sell-through drives tighter, item-specific slots in V2.

### 4.1 Cable-Wrap Post (unique feature)
- A raised cylinder in the center of Zone A. Wind a cable around it before closing the lid.
- Diameter: **10 mm**, Height: **20 mm** (base is 24mm tall — leaves 4mm clearance below the closed lid).
- Printed as a solid, print-in-place cylinder rising from the floor — no overhangs, no supports.

## 5. Lid Body

- Open-bottom shell (built as a box, then shelled removing only the bottom face) — the closed top is the "cap", the walls form a skirt that slides down over the base's outside.
- Skirt height 10mm, cap thickness 1.6mm → lid total height 11.6mm.
- Clearance: lid interior is 0.3mm larger than the base's exterior on each side (0.6mm total per axis) — a friction fit snug enough to stay shut, loose enough to pull off by hand.
- No latch, no hinge, no hardware. Fully removable each time.

## 6. Print Settings (recommended)

| Setting | Value |
|---|---|
| Printer | Generic FDM |
| Material | PLA |
| Nozzle | 0.4 mm |
| Layer height | 0.2 mm |
| Infill | 15% |
| Supports | None required (both bodies print with all cavities open-face-up) |
| Orientation | Base: floor-down. Lid: cap-down (open side up) — both zero-overhang. |

## 7. Estimated Print Time & Material

| | Value |
|---|---|
| Print time (base + lid combined) | ~2.5 hours |
| Material weight (base + lid combined) | ~22 g PLA |

## 8. Fusion File

Saved as **`GearVault_Mini`** in the Fusion "Default Project". Reference renders: [02_Product_Render/GearVault_Mini_iso.png](../02_Product_Render/GearVault_Mini_iso.png).
