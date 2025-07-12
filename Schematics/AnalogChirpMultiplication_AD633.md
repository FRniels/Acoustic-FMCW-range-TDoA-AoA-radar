# Understanding AD633 Analog Multiplier Behavior with Identical Inputs

## Problem Summary
When feeding the same sine wave signal into both X1 and Y1 inputs of the AD633, the output appears:
- Centered above 0V (e.g., ~140 mV)
- At twice the frequency (e.g., 80 kHz if input was 40 kHz)

This might seem counterintuitive, especially when expecting a flat DC output due to zero phase difference.

---

## Core Concept: Multiplication of Identical Sinusoids
If:
```
X(t) = Y(t) = sin(ωt)
```
Then the AD633 performs:
```
W = (X * Y) / 10 = (sin(ωt))^2 / 10
```
Using the trigonometric identity:
```
sin^2(ωt) = 0.5 * (1 - cos(2ωt))
```
So:
```
W = (1/10) * sin^2(ωt)
  = (1/20) * (1 - cos(2ωt))
```
This yields:
- A **DC component** of 1/20 (i.e., 50 mV for 1V peak input)
- A **cosine wave at 2x the input frequency**

---

## Key Takeaways
- The AD633 will always produce a **DC level** plus an **AC ripple at twice the input frequency**, even when both inputs are identical.
- The output is not centered around 0V unless explicitly AC-coupled or offset-corrected.

---

## For Signals Not Centered at 0V
If your signal is 0-3.3V (not centered at 0V), e.g.:
```
X(t) = 1.65 + A * sin(ωt)
```
Then:
```
X^2(t) = (1.65 + A * sin(ωt))^2
       = DC + 1ω + 2ω terms
```
This introduces:
- Even more DC
- Single and double frequency AC terms

---

## Best Practices
- **AC-couple** your signals and center them around 0V before feeding into the multiplier.
- For best phase comparison (e.g. FMCW radar):
  - Ensure both signals are symmetric around 0V
  - Use a **low-pass filter** at the output of the AD633 to isolate the DC term

---

## Conclusion
The AD633 behaves exactly as expected mathematically. The unexpected DC shift and frequency doubling are a natural consequence of squaring a sine wave. For applications like FMCW radar, apply careful AC coupling, proper centering, and LPF design to extract meaningful phase information.

---

*Need help with the low-pass filter design or implementing AC coupling? Just ask!*

