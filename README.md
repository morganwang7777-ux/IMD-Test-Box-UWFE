# IMD-Test-Box-UWFE<img width="1690" height="946" alt="IMD_3DTop" src="https://github.com/user-attachments/assets/2a7c36da-9765-4346-89fd-4fa7007a156a" />


## Test conditions

Test positions, target fault resistances and expected IMD responses come from a chart provided by the UWFE electrical team leads.

| Position | Target fault | Box resistor | Worst-case power | Power at 588 V§ | Expected IMD response |
|---|---|---|---|---|---|
| Open / off | Disconnected | Open circuit | 0 W | 0 W | Normal operation, safe for connecting leads |
| Pass | ≈ 285 kΩ | 270 kΩ | 0.85 W | 1.15 W | Car stays on, well above 147 kΩ |
| Warning | ≈ 500 kΩ | 470 – 485 kΩ | 0.48 W | 0.69 W | Warning over CAN, car stays on |
| Tech fail | 75 kΩ (50% margin) | 60 kΩ | 3.7 W | 3.67 W | Mandatory trip: OK_hs drops, shutdown circuit opens within 30 s |
| Hard short | 15 kΩ (car's own resistor) | 0 Ω, direct wire | 0 W in box (23 W in car) | 0 W in box (23.0 W in car) | Immediate trip, HV to chassis short |

§ I calculated this column myself at the 588 V maximum tractive system voltage, with the car's 15 kΩ TSMP resistor in series: P = (588 V ÷ (box resistor + 15 kΩ))² × box resistor. Warning uses the 470 kΩ chain. Each chain is ten resistors in series, so each resistor takes a tenth of this power, at most 0.37 W, and under 60 V. I split each fault path into ten resistors because no single resistor met both the power and voltage ratings at 588 V.

## Design files

The `Altium/` folder holds the Altium Designer project. Open `IMD test box finale.PrjPcb` to load everything.

| File | Contents |
|---|---|
| `IMD test box finale.PrjPcb` | Altium project |
| `imd finale schematioc.SchDoc` | Schematic |
| `pcb finale.PcbDoc` | Final PCB layout |
| `pcb test.PcbDoc` | Test PCB layout |

`Pics/` has exported images of the schematic, the 2D layout and the 3D board.
