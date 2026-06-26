# Simulation Analysis & Performance Metrics

This file details the electromagnetic behavior of the antenna under simulation.

---

## 1. Return Loss ($S_{11}$) Characterization
The return loss ($S_{11}$) represents the impedance matching behavior across the frequency spectrum. The simulation yields three distinct resonance dips (multiband performance):

```
S11 (dB)
 ^
 0 ┼─────────────────────────────────────────────
   │       \         /     \       /     \
-5 ┼────────\───────/───────\─────/───────\─────
   │         \     /         \   /         \
-10┼──────────\───/───────────\─/───────────\───  <- Threshold (-10 dB)
   │           \ /             V             \
-15┼────────────V            -13.8 dB         V
   │         -13.46 dB      (4.0 GHz)       -16.5 dB
-20┼───────────────────────────────────────(6.7 GHz)──
   └───────┬──────────────┬──────────────┬──────> Freq (GHz)
          2.4            4.0            6.7
```

* **Primary Resonance (2.4 GHz):** The return loss reaches **$-13.47	ext{ dB}$**, indicating strong coupling to the 50-ohm transmission line at the target ISM frequency.
* **Secondary Resonances (4.0 GHz & 6.7 GHz):** The fractal slots modify high-order surface current pathways, creating secondary resonant nodes. This makes the design suitable for multi-frequency applications.

---

## 2. Voltage Standing Wave Ratio (VSWR)
The VSWR indicates the power matching efficiency:
* **VSWR at 2.4 GHz:** $pprox 1.54$
* **Interpretation:** A value below 2.0 confirms that the reflection loss is minimal, and the antenna is suitable for deployment in hardware prototypes.

---

## 3. Radiation Pattern Characteristics
* **E-Plane (Electric Field):** Shows a stable bi-directional radiation profile resembling a classic dipole radiation pattern.
* **H-Plane (Magnetic Field):** Exhibits near-omnidirectional behavior, which is ideal for mobile wireless transceivers (Wi-Fi/Bluetooth) where signal orientation is dynamic.
