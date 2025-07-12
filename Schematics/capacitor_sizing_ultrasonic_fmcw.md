
# Capacitor Sizing for AC Coupling in Ultrasonic FMCW System

## 🎯 Goal
Ensure all AC coupling and biasing capacitors have **low reactance at 40 kHz**, the operating frequency of the ultrasonic chirp.

---

## 📐 Design Rule

Use:

```
Xc = 1 / (2 * π * f * C)
```

Where:
- `Xc` = Capacitive reactance (Ω)
- `f` = Frequency (Hz)
- `C` = Capacitance (F)

To **minimize signal attenuation**, choose:
```
Xc << R  →  typically Xc < R / 10
```

---

## ✅ Example Calculation

Assuming:
- `f` = 40 kHz
- `R` = 47kΩ (e.g. Ri in gain stage)

Then:
```
Xc ≤ 4.7kΩ
C ≥ 1 / (2 * π * 40,000 * 4700) ≈ 0.85 nF
```

---

## 🔧 Recommended Values

| Capacitor Location           | Suggested Value      |
|-----------------------------|----------------------|
| Inter-stage coupling         | 10 nF – 100 nF       |
| Series with Ri (bias input) | 10 nF – 100 nF       |
| Rx input coupling cap        | 100 nF – 1 µF        |

> ✅ For simplicity and reliability, using **100 nF** ceramic caps throughout is a solid choice.

---

## 📎 Notes

- Values higher than calculated are fine, as long as they don't create unwanted low-pass filtering with surrounding resistors.
- Keep an eye on physical cap size when using >1 µF, especially in through-hole prototyping.
