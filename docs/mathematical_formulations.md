# Antenna Mathematical Formulations & Analytical Models

This document presents the mathematical framework and equations used to design, size, and validate the **Compact Hexagonal Fractal Patch Antenna**.

---

## 1. Transmission Line Model for the Reference Patch
Before introducing fractal slots, the dimensions of a reference microstrip patch antenna must be analytically calculated. The patch is modeled as a slot radiator separated by a transmission line of length $L$.

### Step 1: Calculation of Patch Width ($W$)
The physical width of the patch is calculated to ensure high radiation efficiency:
$$W = \frac{c}{2 f_r} \sqrt{\frac{2}{\epsilon_r + 1}}$$

Where:
* $c = 3 \times 10^8 \text{ m/s}$ (Speed of light in free space)
* $f_r = 2.4 \times 10^9 \text{ Hz}$ (Target resonant frequency)
* $\epsilon_r = 4.4$ (Substrate relative permittivity)

Substituting the values:
$$W = \frac{3 \times 10^8}{2 \times (2.4 \times 10^9)} \sqrt{\frac{2}{4.4 + 1}} = 0.0625 \times \sqrt{0.3703} \approx 38.03 \text{ mm}$$

---

### Step 2: Calculation of Effective Dielectric Constant ($\epsilon_{reff}$)
Because electromagnetic fields travel through both the substrate and the air above it, an effective dielectric constant is calculated:
$$\epsilon_{reff} = \frac{\epsilon_r + 1}{2} + \frac{\epsilon_r - 1}{2} \left[ 1 + 12\frac{h}{W} \right]^{-1/2}$$

Where:
* $h = 1.6 \text{ mm}$ (Substrate thickness)

Substituting the values:
$$\epsilon_{reff} = \frac{4.4 + 1}{2} + \frac{4.4 - 1}{2} \left[ 1 + 12\left(\frac{1.6}{38.03}\right) \right]^{-1/2} \approx 2.7 + 1.7 \times [1.5048]^{-1/2} \approx 4.08$$

---

### Step 3: Calculation of Extension Length ($\Delta L$)
Fringing fields along the edges make the patch look electrically longer than its physical length. This extension $\Delta L$ is given by:
$$\Delta L = 0.412 h \frac{(\epsilon_{reff} + 0.3) \left( \frac{W}{h} + 0.264 \right)}{(\epsilon_{reff} - 0.258) \left( \frac{W}{h} + 0.8 \right)}$$

Using our parameters ($W/h \approx 23.77$), $\Delta L \approx 0.74 \text{ mm}$.

---

### Step 4: Physical Length of the Reference Patch ($L$)
The actual physical length of the patch is:
$$L = \frac{c}{2 f_r \sqrt{\epsilon_{reff}}} - 2\Delta L$$

Substituting the values:
$$L = \frac{3 \times 10^8}{2 \times (2.4 \times 10^9) \sqrt{4.08}} - 2(0.00074) \approx 30.95 \text{ mm} - 1.48 \text{ mm} = 29.47 \text{ mm}$$

---

## 2. Hexagonal Transformation & Equilateral Geometry
A hexagon can be defined by its side length $s$. The area of a regular hexagon is:
$$A_{hex} = \frac{3\sqrt{3}}{2} s^2 \approx 2.598 s^2$$

To maintain frequency equivalence, the area of the regular hexagon is matched to the equivalent rectangular patch area ($A_{rect} = W \times L$):
$$A_{hex} \approx A_{rect} \implies 2.598 s^2 \approx 38.03 \times 29.47 \implies s \approx 20.76 \text{ mm}$$

This side length $s$ yields a maximum diagonal width ($2s \approx 41.52 \text{ mm}$), which matches the optimized dimension $b = 41.69 \text{ mm}$ in HFSS.

---

## 3. Return Loss and Reflection Coefficients
The performance of impedance matching is characterized by the Reflection Coefficient ($\Gamma$), S-parameter ($S_{11}$), and Voltage Standing Wave Ratio ($VSWR$):

### S11 to Reflection Coefficient Conversion
$$S_{11} (\text{dB}) = 20 \log_{10} |\Gamma|$$

At the resonant frequency ($S_{11} = -13.46 \text{ dB}$):
$$-13.46 = 20 \log_{10} |\Gamma| \implies |\Gamma| = 10^{-13.46/20} \approx 0.2123$$

### VSWR Calculation
$$VSWR = \frac{1 + |\Gamma|}{1 - |\Gamma|}$$

Substituting $|\Gamma| = 0.2123$:
$$VSWR = \frac{1 + 0.2123}{1 - 0.2123} = \frac{1.2123}{0.7877} \approx 1.539 \approx 1.54$$

A $VSWR < 2$ indicates that more than **95.5% of the input power** is successfully delivered to the antenna patch, with less than 4.5% reflected back, representing excellent industrial matching performance.
