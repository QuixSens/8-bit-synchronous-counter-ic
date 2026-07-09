# 8-bit Synchronous Counter IC

Transistor-level design of an 8-bit synchronous counter IC using custom CMOS logic, built in Cadence Virtuoso on the 180nm PDK. Integrates a Parallel-In Serial-Out (PISO) shift register and 8-bit Counter to produce a 10-cycle serial output sequence with active-low reset.

## Key Specifications

| Parameter | Value |
|---|---|
| Technology | 180nm CMOS |
| Design Tool | Cadence Virtuoso |
| Counter Width | 8-bit |
| Output Protocol | 10-cycle serial output |
| Reset | Active-low |
| Verification | DRC, LVS, PEX — clean sign-off |

## Design Architecture

- **Counter core** — synchronous 8-bit counter implemented at the transistor level
- **PISO shift register** — parallel-loads the counter output and shifts it out serially
- **8-bit Counter** — UP counts at every positive clock edge from 0 to 256 when enable(EN) is high.

## Key Challenge & Debugging

During verification, a timing bug surfaced where the EN and LOAD control signals were asserted on the same clock edge, corrupting the serial output. The issue was traced to transition logic and resolved by correcting the control signal timing, restoring correct functional behavior — confirmed through post-layout simulation.

## Repository Structure

```
├── docs/
│   ├── lab_report.pdf
│   ├── gate_datasheets/
│   └── module_datasheets/
├── schematics/
│   ├── piso_shift_register.png
│   └── counter
├── layout/
│   ├── counter.png
│   └── module
│   └── piso_shift_register
├── images/
│   └── timing_waveforms/
└── README.md
```

## Tools Used

`Cadence Virtuoso` `180nm PDK` `Custom CMOS Design`
