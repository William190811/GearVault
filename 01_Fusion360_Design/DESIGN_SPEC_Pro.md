# GearVault Pro — Design Spec

Handoff document for modeling in Fusion 360 (intended for a Claude Code + Fusion 360 MCP session). This spec should be precise enough to model directly from without further clarification. GearVault Pro shares **one Fusion 360 feature tree** with GearVault Mini (see `DESIGN_SPEC_Mini.md`) — only parameter values and the added SD/dongle tray feature differ.

## 1. Overview

GearVault Pro is the larger of two size variants of the GearVault parametric design — a hard-shell, snap-lid organizer pod for loose backpack peripherals (earbuds, USB drives, cables, dongles). Pro sits right at the assignment's maximum allowed footprint.

Two bodies:
- **Base** — compartment tray + integrated cable-wrap post + hinge sockets
- **Lid** — shell + hinge lugs + snap ridge

## 2. Overall Envelope

| Dimension | Value |
|---|---|
| Outer length (X) | 80 mm |
| Outer width (Y) | 80 mm |
| Outer height (Z), lid closed | 38 mm |
| Assignment max allowed | 80 x 80 x 80 mm — Pro is at the X/Y cap, well under the Z cap |

Approximate height split: Base 24 mm tall (walls) + Lid 16 mm tall (shell), overlapping at a 2 mm lap joint where the lid skirt seats over the base rim (included in the 38 mm total, not additive).

## 3. Wall / Floor / Fillet Rules (apply to both bodies — same as Mini)

| Feature | Minimum |
|---|---|
| Side wall thickness | 1.6 mm |
| Floor thickness (base) / ceiling thickness (lid) | 1.2 mm |
| External edge fillets | 1.0 mm radius (all outer edges, top and bottom perimeter edges of both shells) |
| Internal compartment divider walls | 1.6 mm |

## 4. Base Body — Compartment Layout

Base interior floor sits 1.2 mm above the base's bottom face. All compartments open upward (face-up), so the part prints with the base floor flat on the print bed and pockets/cavities opening toward +Z — zero overhangs requiring support.

Interior usable footprint (inside the 1.6 mm walls): approx. 76.8 x 76.8 mm.

### 4.1 Earbud Pocket
- Shape: rounded-rectangle pocket, single cavity (case-style), sized for a typical wireless-earbud charging case.
- Internal dimensions: **48 mm (L) x 30 mm (W) x 16 mm (D)** — same as Mini (earbud case size doesn't scale with pod size), corner fillets 3 mm internal radius.
- Positioned in one corner/edge of the base, floor of pocket flush with base floor (1.2 mm above bottom face).

### 4.2 USB-Drive Slots (x4)
- Reference part: standard USB-A stick, approx. 12 x 45 x 6 mm (W x L x H).
- Slot internal dimensions (friction-fit, +0.4 mm clearance each on W and H): **12.4 mm (W) x 46 mm (L, open-ended) x 6.4 mm (H)** — same slot dimensions as Mini.
- Slot floor sits on the base floor (open-top U-channel: floor + two 1.6 mm side walls, open top, open one end for finger access).
- Four slots arranged in a row (or 2x2 block if a row doesn't fit the footprint alongside other compartments), each separated by a shared 1.6 mm divider wall, total row footprint approx. (4 x 12.4) + (5 x 1.6) = ~57.6 mm along the row.
- Located along one side of the base, opposite the earbud pocket.

### 4.3 SD-Card / Dongle Tray (Pro only, added feature)
- A shallow open tray for SD cards, micro-SD adapters, small USB-C/Bluetooth dongles.
- Internal dimensions: **35 mm (L) x 25 mm (W) x 8 mm (D)**, wall thickness 1.6 mm, floor flush with base floor.
- Optional internal divider (single 1.6 mm rib down the middle, splitting the tray into two ~16.5 mm-wide sub-bays) to keep SD cards from sliding around — recommended but not structurally required.
- Positioned in the remaining open corner of the base (opposite the USB slot row, adjacent to or below the earbud pocket), sized to fit within the leftover floor area alongside the cable-wrap post.

### 4.4 Cable-Wrap Post (unique feature)
- A raised cylindrical peg molded into the center of the base floor. Cable is wound around it before closing the lid — prevents tangling.
- Diameter: **10 mm** (same as Mini — post size doesn't need to scale with pod footprint)
- Height: **18 mm** (taller than Mini's 14 mm to make use of Pro's greater internal height, leaving approx. 2 mm gap under the closed lid at 38 mm total height)
- Fillet at post base: 1 mm radius (stress relief + zero-support printability)
- Position: geometric center of the remaining open floor area between the earbud pocket, USB slot row, and SD/dongle tray.
- Printed as a solid, print-in-place cylinder rising straight from the floor in +Z — no overhangs, no supports needed.

## 5. Lid Body

- Outer shell matching base's outer footprint (80 x 80 mm plan), shell wall 1.6 mm, ceiling 1.2 mm thick.
- Lid skirt (downward-facing lip, 2 mm deep) overlaps the base's top rim when closed.
- Snap ridge: continuous internal ridge along the inside of the lid's front edge (opposite the hinge edge), 0.8 mm tall x 1.0 mm wide, clicking past a mating lip on the base's front wall top edge. Both surfaces get a 0.5 mm, 45-degree lead-in chamfer for easy thumb-opening.

## 6. Hinge (print-in-place snap-pin friction hinge)

Same geometry family as Mini, scaled only in lug count/spacing to suit the wider (80 mm) hinge edge. Pin axis horizontal, parallel to the print bed — zero support.

| Feature | Value |
|---|---|
| Lug (on Lid) diameter | 4.0 mm |
| Lug width (each, along hinge axis) | 4 mm |
| Number of lugs | 2, placed 12 mm in from each side edge (wider spacing than Mini to suit the 80 mm edge, improves resistance to lid racking) |
| Socket (in Base) internal diameter | 4.2 mm (lug diameter + 0.2 mm radial clearance) |
| Socket width | 4.6 mm (0.3 mm axial clearance each side) |
| Socket wall (retaining lip) | C-shaped clip (270 degree wrap), same as Mini, for support-free printing and hand assembly |
| Hinge pin axis height | centered at 12 mm above the base's bottom face (proportionally similar position to Mini, adjusted for Pro's taller 24 mm base wall) |

Clearance tolerance for the fit: **+/-0.2 mm** on the lug/socket diametrical clearance (same as Mini — track adjustments in `03_Design_Process/DESIGN_PROCESS_LOG.md`).

## 7. Print Settings (recommended)

| Setting | Value |
|---|---|
| Printer | Generic FDM |
| Material | PLA |
| Nozzle | 0.4 mm |
| Layer height | 0.2 mm |
| Infill | 15% |
| Supports | None required |
| Orientation | Base: floor-down, compartments face up. Lid: outer shell face-down, interior face up (snap ridge and hinge lugs print without overhangs). |
| Print-in-place hinge gap | Print base and lid as separate bodies (same or separate jobs); hinge assembled by hand after printing. |

Note: Pro's larger footprint (80x80 mm) approaches typical FDM bed-adhesion limits for tall thin-walled parts — a brim (2-3 mm) is recommended on both bodies to reduce warping risk, even though no supports are needed.

## 8. Estimated Print Time & Material

| | Value |
|---|---|
| Print time (base + lid combined) | ~4 hours |
| Material weight (base + lid combined) | ~38 g PLA |

## 9. Parametric Modeling Notes (shared Mini/Pro feature tree)

Pro uses the same user-parameter set defined in `DESIGN_SPEC_Mini.md` Section 9, with these values:

- `outer_length` = 80, `outer_width` = 80, `outer_height` = 38
- `wall_thickness` = 1.6, `floor_thickness` = 1.2, `edge_fillet_radius` = 1.0 (unchanged from Mini)
- `earbud_pocket_length` = 48, `earbud_pocket_width` = 30, `earbud_pocket_depth` = 16 (unchanged from Mini)
- `usb_slot_width` = 12.4, `usb_slot_length` = 46, `usb_slot_height` = 6.4 (unchanged from Mini), `usb_slot_count` = 4
- `sd_tray_length` = 35, `sd_tray_width` = 25, `sd_tray_depth` = 8 (Pro-only feature; suppressed/zeroed in the Mini configuration)
- `cable_post_diameter` = 10 (unchanged), `cable_post_height` = 18 (taller than Mini's 14)
- `hinge_lug_diameter` = 4.0, `hinge_socket_clearance` = 0.2 (unchanged from Mini), lug inset from edge = 12 mm (vs. Mini's 10 mm — can also be parameterized as `hinge_lug_inset`)
- `snap_ridge_height`, `snap_ridge_width` (unchanged from Mini)

Keep Pro as a separate Fusion 360 document (or a second configuration in the same parametric design) referencing these same parameter names and the same feature order as Mini, so the SD/dongle tray is the only feature that needs to be added/suppressed between the two configurations — every other feature is a pure parameter-value change.
