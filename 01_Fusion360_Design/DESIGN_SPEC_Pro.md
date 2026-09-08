# GearVault Pro — Design Spec (as-built V1.1)

Saved as its own Fusion 360 cloud design: **`GearVault_Pro`** (Default Project, separate document from Mini). Native source archived at [CAD_Source/GearVault_Pro.f3d](CAD_Source/GearVault_Pro.f3d); print-ready meshes at [STL/GearVault_Pro_Base.stl](STL/GearVault_Pro_Base.stl) and [STL/GearVault_Pro_Lid.stl](STL/GearVault_Pro_Lid.stl).

## 1. Overview

Same construction as Mini (see `DESIGN_SPEC_Mini.md` for the shared build notes / API gotchas), scaled wider to add an accessory lane alongside the case bay for USB drives, SD cards, and dongles:
- **Base** — open-top tray: **earbud-case bay** + wider **accessory lane** (USB/SD/dongles + cable-wrap post)
- **Lid** — open-bottom friction-fit slip cap, **"GearVault" engraved** into the top

## 2. Overall Envelope

| Dimension | Value |
|---|---|
| Base outer (L x W x H) | 69 x 75 x 30 mm |
| Lid outer (L x W x H) | 72.8 x 78.8 x 13.6 mm (slides over the base's outside) |
| **Assembled (lid on) footprint** | **72.8 x 78.8 x 30 mm** |
| Assignment max allowed | 80 x 80 x 80 mm |

**Sizing note:** since the lid telescopes over the base's outside, the assembled footprint is the lid's size, not the base's. The base is sized at 75mm (width) specifically so the assembled unit lands at 78.8mm — under the 80mm cap.

## 3. Wall / Fillet Rules (both bodies — same as Mini)

| Feature | Value |
|---|---|
| Wall + floor/ceiling thickness | 1.6 mm (uniform) |
| External vertical-edge fillets | 2.0 mm radius |
| Divider wall thickness | 1.6 mm |

## 4. Base Body — Compartment Layout

Interior split by **one divider running the full length** (same length as Mini's case bay, so both variants share the same case-bay footprint):

- **Case bay**: clear **65.8 x 50.0 mm** — identical footprint to Mini's, same real-earbud-case fit (see `DESIGN_SPEC_Mini.md` Section 4 for the reference case envelope).
- **Accessory lane**: clear **65.8 x 20.2 mm** — wider than Mini's cable lane to also hold loose USB drives and SD cards/dongles alongside the cable-wrap post.

### 4.1 Cable-Wrap Post (unique feature)
- Diameter: **10 mm**, Height: **24 mm** (base is 30mm tall — leaves ~4.4mm clearance below the closed lid).
- Centered in the accessory lane.

## 5. Lid Body

- Open-bottom shell: skirt height 12mm + 1.6mm cap = 13.6mm total.
- Clearance: 0.3mm per side (same as Mini).
- **Engraved "GearVault" wordmark** on the top face, centered, ~5mm tall, 0.4mm deep.
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
| Orientation | Base: floor-down. Lid: cap-down (open side up), engraving faces up. |

Pro's larger footprint is closer to typical bed-adhesion limits for a tall thin-walled part — a brim (2–3mm) is recommended on both bodies.

## 7. Estimated Print Time & Material

| | Value |
|---|---|
| Print time (base + lid combined) | ~4 hours |
| Material weight (base + lid combined) | ~38 g PLA |
