# Manufacturing Plan — GearVault

Default process assumption (printer/material not yet chosen): generic FDM
printer, PLA filament, 0.4mm nozzle, 0.2mm layer height. Team is producing
5x Mini + 5x Pro = 10 units total. Costs referenced in Indonesian Rupiah
(IDR).

Structured around the "think like a manufacturer" questions from the
assignment brief:

| Question | Answer |
|---|---|
| How long does one unit take to print? | Mini: ~2.5 hr/unit. Pro: ~4 hr/unit. |
| How much material does it use? | Mini: ~22 g PLA/unit. Pro: ~38 g PLA/unit. Total for 10 units (5 Mini + 5 Pro): ~300 g, plus a 15% failure buffer (~45 g) = **~345 g PLA** to have on hand. |
| What happens if a print fails? | Two known failure risks: (1) lid warping — mitigate by printing with a brim; (2) hinge lugs too tight or snapping — mitigate by test-fitting hinge tolerance to ±0.2mm before committing to a full batch. |
| Does it require assembly? | Minimal — snap-fit only, no glue or hardware, ~30 seconds per unit. |
| How will you package it? | Small kraft drawstring pouch, or a printed cardstock sleeve with the GearVault logo and a QR code linking to the feedback form. |

## Batch Strategy

Print one Mini and one Pro as a first test unit before committing the rest
of the material. Use these two test units to verify hinge fit (does the lid
snap and rotate cleanly at the printed tolerance?) and wall strength (does
the 2mm wall hold up to normal handling and squeezing?) before touching
anything else. Only after both test units pass fit and durability checks
does the team move to printing the remaining 8 units (4 Mini + 4 Pro) as a
batch. This sequencing exists specifically to catch the two known failure
risks (warping, hinge tolerance) on a cheap 2-unit test instead of on a full
10-unit run.
