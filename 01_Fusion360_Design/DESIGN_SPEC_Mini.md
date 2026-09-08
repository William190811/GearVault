# GearVault Mini — Design Spec (as-built V1.1)

Saved as its own Fusion 360 cloud design: **`GearVault_Mini`** (Default Project). Native source archived at [CAD_Source/GearVault_Mini.f3d](CAD_Source/GearVault_Mini.f3d); print-ready meshes at [STL/GearVault_Mini_Base.stl](STL/GearVault_Mini_Base.stl) and [STL/GearVault_Mini_Lid.stl](STL/GearVault_Mini_Lid.stl).

## 1. Overview

Two bodies, modeled as separate solids in their own Fusion document (kept separate from Pro's document, per team preference for one file per size):
- **Base** — open-top tray: one large **earbud-case bay** + a narrow **cable lane** with the cable-wrap post, divided by a single wall
- **Lid** — open-bottom friction-fit slip cap, with **"GearVault" engraved** into the top

### Revision note (V1.1)
The first pass at this compartment layout undersized the earbud pocket relative to a real charging case. Reworked so the case bay is sized to a real-world case envelope (see Section 4) instead of an arbitrary pocket, and moved the cable-wrap post into its own narrow lane alongside the case bay so it doesn't compete for space with — or get blocked by — the case itself.

## 2. Overall Envelope

| Dimension | Value |
|---|---|
| Base outer (L x W x H) | 69 x 65 x 29 mm |
| Lid outer (L x W x H) | 72.8 x 68.8 x 11.6 mm (slides over the base's outside) |
| **Assembled (lid on) footprint** | **72.8 x 68.8 x 29 mm** |
| Assignment max allowed | 80 x 80 x 80 mm |

## 3. Wall / Fillet Rules (both bodies)

| Feature | Value |
|---|---|
| Wall + floor/ceiling thickness | 1.6 mm (uniform) |
| External vertical-edge fillets | 2.0 mm radius |
| Divider wall thickness | 1.6 mm |

## 4. Base Body — Compartment Layout

Interior split by **one divider running the full length**, parallel to the long axis, so the case bay gets the full 65.8mm length:

- **Case bay**: clear **65.8 x 50.0 mm**, full interior height (27.4mm clear). Sized to fit real wireless-earbud charging cases with margin — reference envelope used: up to ~61 x 48 x 27mm (covers AirPods 60.6x44.3x21.7mm, AirPods Pro 45.2x60.6x21.7mm, Galaxy Buds-family cases ~50x38x27mm, and similar). The case sits loose in this bay; the cable-wrap post occupies the adjacent lane so it never blocks the case.
- **Cable lane**: clear **65.8 x 10.2 mm**, alongside the case bay. Holds the cable-wrap post; a charging cable coils around the post here.

### 4.1 Cable-Wrap Post (unique feature)
- Diameter: **8 mm**, Height: **22 mm** (base is 29mm tall — leaves ~5.4mm clearance below the closed lid).
- Centered in the cable lane.

## 5. Lid Body

- Open-bottom shell: skirt height 10mm + 1.6mm cap = 11.6mm total.
- Clearance: 0.3mm per side for a snug friction fit.
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

## 7. Estimated Print Time & Material

| | Value |
|---|---|
| Print time (base + lid combined) | ~2.5 hours |
| Material weight (base + lid combined) | ~22 g PLA |

## 8. Build notes for whoever models this next (Fusion API gotchas hit during this build)

- **Finding a horizontal face by `Plane.origin.z` alone is unreliable** — vertical side faces can also report `origin.z ≈ 0` (their plane's reference origin isn't necessarily at a "nice" point). Always also check the face normal (`abs(abs(normal.z) - 1.0) < 1e-6`) before matching on z-position. This bug silently opened a side wall instead of the lid's bottom on the first attempt.
- **`SketchText` doesn't produce usable extrude profiles until you call `sketchText.explode()`** on it first. Before exploding, `sketch.profiles` only contains the sketch's auto-generated face-boundary profile (the whole face, not the letters) — cutting with that removes/lowers the entire face instead of engraving text.
- **Extrude/cut direction**: `setDistanceExtent(False, value)` extrudes in the profile normal's positive direction by default, which for a sketch on a model's outward-facing top face is *away* from the material. Use a **negative** distance value to cut inward/downward when engraving on a top face.
- **Cloud save requires an active Fusion license/entitlement.** `Document.saveAs()` returns `True` even when the cloud upload silently fails without one — check `doc.isSaved` after, don't trust the return value alone.
