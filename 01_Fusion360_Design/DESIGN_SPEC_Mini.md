# GearVault Mini — Design Spec

Handoff document for modeling in Fusion 360 (intended for a Claude Code + Fusion 360 MCP session). This spec should be precise enough to model directly from without further clarification.

## 1. Overview

GearVault Mini is the smaller of two size variants of the GearVault parametric design — a hard-shell, snap-lid organizer pod for loose backpack peripherals (earbuds, USB drives, cables, dongles). Mini and Pro share **one Fusion 360 feature tree**; only parameter values differ between them (see Section 8).

Two bodies:
- **Base** — compartment tray + integrated cable-wrap post + hinge sockets
- **Lid** — shell + hinge lugs + snap ridge

## 2. Overall Envelope

| Dimension | Value |
|---|---|
| Outer length (X) | 70 mm |
| Outer width (Y) | 55 mm |
| Outer height (Z), lid closed | 32 mm |
| Assignment max allowed | 80 x 80 x 80 mm (Mini is well under cap) |

Approximate height split: Base 20 mm tall (walls) + Lid 12 mm tall (shell), overlapping at a 2 mm lap joint where the lid skirt seats over the base rim (included in the 32 mm total, not additive).

## 3. Wall / Floor / Fillet Rules (apply to both bodies)

| Feature | Minimum |
|---|---|
| Side wall thickness | 1.6 mm |
| Floor thickness (base) / ceiling thickness (lid) | 1.2 mm |
| External edge fillets | 1.0 mm radius (all outer edges, top and bottom perimeter edges of both shells) |
| Internal compartment divider walls | 1.6 mm |

## 4. Base Body — Compartment Layout

Base interior floor sits 1.2 mm above the base's bottom face (the floor thickness). All compartments open upward (face-up), so the part prints with the base floor flat on the print bed and pockets/cavities opening toward +Z — zero overhangs requiring support.

Interior usable footprint (inside the 1.6 mm walls): approx. 66.8 x 51.8 mm.

### 4.1 Earbud Pocket
- Shape: rounded-rectangle pocket, single cavity (case-style, not per-bud), sized for a typical wireless-earbud charging case.
- Internal dimensions: **48 mm (L) x 30 mm (W) x 16 mm (D)**, corner fillets 3 mm internal radius.
- Positioned in one end of the base (e.g. left third), floor of pocket is a flat shelf at 1.2 mm above base bottom (matches base floor thickness — no separate raised floor needed here).

### 4.2 USB-Drive Slots (x2)
- Reference part: standard USB-A stick, approx. 12 x 45 x 6 mm (W x L x H).
- Slot internal dimensions (friction-fit, +0.4mm clearance each on W and H to allow insertion without being loose): **12.4 mm (W) x 46 mm (L, open-ended slot, drive can protrude slightly) x 6.4 mm (H)**.
- Slot floor sits on the base floor (open-top channel, drive slides in vertically from above and rests in the horizontal channel — printed as a U-shaped channel: floor + two 1.6 mm side walls, open top, open one end for easy finger access).
- Two slots placed side by side, wall-to-wall spacing 1.6 mm (shared divider) between them, located in the opposite end of the base from the earbud pocket.

### 4.3 Cable-Wrap Post (unique feature)
- A raised cylindrical peg molded into the center of the base floor. Cable is wound around it before closing the lid — prevents tangling.
- Diameter: **10 mm**
- Height: **14 mm** (tall enough to keep a wound cable below the lid's inner ceiling clearance, leaving approx. 2 mm gap under the closed lid)
- Fillet at post base: 1 mm radius (stress relief + zero-support printability — solid cylinder printed straight up from the floor needs no support)
- Position: geometric center of the remaining open floor area between the earbud pocket and the USB slots (approx. centered in the base's middle third).
- Printed as a solid, print-in-place cylinder rising straight from the floor in +Z — no overhangs, no supports needed.

## 5. Lid Body

- Outer shell matching base's outer footprint (70 x 55 mm plan), shell wall 1.6 mm, ceiling 1.2 mm thick.
- Lid skirt (downward-facing lip, 2 mm deep) overlaps the base's top rim when closed, for dust/rattle control — does not need to be watertight, just a visual/mechanical registration lip.
- Snap ridge: a continuous internal ridge running along the inside of the lid's front edge (opposite the hinge edge), 0.8 mm tall x 1.0 mm wide, that clicks past a mating lip printed on the base's front wall top edge to hold the lid shut. Both ridge and mating lip get a 45-degree lead-in chamfer (0.5 mm) on their engagement faces so the snap can flex open with light thumb pressure without a screwdriver.

## 6. Hinge (print-in-place snap-pin friction hinge)

Two-lug, two-socket, standard print-in-place snap-hinge geometry positioned along the rear edge (55 mm-wide edge) of both bodies, so the hinge pin axis is horizontal and parallel to the print bed — printable with zero support.

| Feature | Value |
|---|---|
| Lug (on Lid) diameter | 4.0 mm |
| Lug width (each, along hinge axis) | 4 mm |
| Number of lugs | 2, placed 10 mm in from each side edge |
| Socket (in Base) internal diameter | 4.2 mm (lug diameter + 0.2 mm radial clearance for friction fit rotation) |
| Socket width | 4.6 mm (0.3 mm axial clearance each side for free rotation without wobble) |
| Socket wall (retaining lip around opening) | printed as a C-shaped clip (270 degree wrap) so the lug can be snapped in during/after printing without support inside the socket bore |
| Hinge pin axis height | centered at 10 mm above the base's bottom face (aligned with the base wall's top region) |

Clearance tolerance for the fit: **+/-0.2 mm** on the lug/socket diametrical clearance — this is the dimension most likely to need print-test tuning (see `03_Design_Process/DESIGN_PROCESS_LOG.md`).

Both lugs and sockets are modeled as horizontal cylinders (axis parallel to the X or Y bed plane, not vertical), which is the standard zero-support orientation for print-in-place snap hinges on FDM printers — the circular cross-section prints as a series of stacked, self-supporting arcs.

## 7. Print Settings (recommended)

| Setting | Value |
|---|---|
| Printer | Generic FDM |
| Material | PLA |
| Nozzle | 0.4 mm |
| Layer height | 0.2 mm |
| Infill | 15% (functional but not load-bearing; walls/floor thickness carry structural duty) |
| Supports | None required |
| Orientation | Base: floor-down, compartments face up. Lid: outer shell face-down (convex face down), interior face up, so the snap ridge and hinge lugs print without overhangs. |
| Print-in-place hinge gap | Print base and lid as separate bodies in the same job (or separate jobs) — the hinge is assembled by hand (snap lugs into sockets) after printing, not printed already interlocked, to guarantee full print reliability at this scale. |

## 8. Estimated Print Time & Material

| | Value |
|---|---|
| Print time (base + lid combined) | ~2.5 hours |
| Material weight (base + lid combined) | ~22 g PLA |

## 9. Parametric Modeling Notes (for shared Mini/Pro feature tree)

Model both sizes from a single Fusion 360 feature tree by driving these dimensions as **user parameters** (same parameter names in both design files, different values):

- `outer_length`, `outer_width`, `outer_height` (envelope — Mini: 70/55/32, Pro: 80/80/38)
- `wall_thickness` (constant 1.6 mm both sizes)
- `floor_thickness` (constant 1.2 mm both sizes)
- `edge_fillet_radius` (constant 1.0 mm both sizes)
- `earbud_pocket_length`, `earbud_pocket_width`, `earbud_pocket_depth`
- `usb_slot_width`, `usb_slot_length`, `usb_slot_height`, `usb_slot_count` (Mini: 2, Pro: 4 — drive the USB slot array with a rectangular pattern feature referencing this count)
- `sd_tray_length`, `sd_tray_width`, `sd_tray_depth` (Pro only — set to 0 / suppress the feature for Mini, or keep as a separate feature only present in the Pro-configured tree if a single-tree suppression approach is used)
- `cable_post_diameter`, `cable_post_height` (constant 10 / 14 mm both sizes — same post size works for both; do not scale with envelope)
- `hinge_lug_diameter`, `hinge_socket_clearance` (constant across both sizes: 4.0 mm lug, 0.2 mm radial clearance)
- `snap_ridge_height`, `snap_ridge_width` (constant both sizes)

Recommendation: keep the two sizes as two separate Fusion 360 documents (or two configurations within one parametric design if using Fusion's configuration tools), both referencing the same named parameters and the same feature order, so a change to the feature tree logic (e.g. snap ridge shape) can be ported between them by copying feature definitions rather than rebuilding geometry.
