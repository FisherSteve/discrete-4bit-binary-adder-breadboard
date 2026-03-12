# Discrete 4-Bit Binary Adder (Breadboard Edition)

Ein von Grund auf diskret aufgebauter 4-Bit-Binäraddierer auf dem Breadboard, inspiriert durch die Hardware-Projekte von **Ben Eater**. [cite_start]Dieses Projekt demonstriert die fundamentale Funktionsweise von Computer-Arithmetik durch die physische Verschaltung einzelner Logikgatter der 74HC-Serie[cite: 1, 2].

## 🚀 Projektübersicht

Anstatt fertige Addierer-Chips zu verwenden, nutzt dieses Design grundlegende Logikgatter (XOR, AND, OR), um zu zeigen, wie ein Computer "denkt". [cite_start]Die Schaltung berechnet die Summe zweier 4-Bit-Zahlen ($A$ und $B$) und gibt das Ergebnis über fünf LEDs aus[cite: 1, 2].

### Kernmerkmale:
* [cite_start]**Ripple Carry Architektur:** Der Übertrag (Carry) wandert sequenziell durch jede Bit-Stufe[cite: 1].
* [cite_start]**Hybrid-Design:** Bestehend aus 1x Half Adder (für Bit 0) und 3x Full Adder (für die Bits 1-3)[cite: 1].
* [cite_start]**Visuelles Feedback:** Direkte Anzeige der Binärwerte über LEDs ($s_0$ bis $s_3$ und der finale Carry-Out $c_3$)[cite: 1, 2].

---

## 📐 Logik & Wahrheitstabelle

Die Schaltung basiert auf den Standard-Logikfunktionen für Addition:
* **Summe ($S$):** $A \oplus B \oplus C_{in}$
* **Übertrag ($C_{out}$):** $(A \cdot B) + (C_{in} \cdot (A \oplus B))$

### Testfälle zur Validierung:

| Zahl A ($a_3 a_2 a_1 a_0$) | Zahl B ($b_3 b_2 b_1 b_0$) | Übertrag ($c_3$) | Summe ($s_3 s_2 s_1 s_0$) | Ergebnis (Dezimal) |
| :--- | :--- | :--- | :--- | :--- |
| `0001` (1) | `0001` (1) | `0` | `0010` | 2 |
| `0011` (3) | `0001` (1) | `0` | `0100` | 4 |
| `0111` (7) | `0001` (1) | `0` | `1000` | 8 |
| `1111` (15) | `0001` (1) | `1` | `0000` | 16 (Überlauf) |
| `1010` (10) | `0101` (5) | `0` | `1111` | 15 |

---

## 🛠 Hardware & Stückliste (BOM)

Das Projekt ist für eine Spannungsversorgung von **5V (USB)** ausgelegt.

| Komponente | Menge | Details |
| :--- | :--- | :--- |
| **74HC86** | 2 | Quad XOR-Gatter (Summenbildung) |
| **74HC08** | 2 | Quad AND-Gatter (Carry-Logik) |
| **74HC32** | 1 | Quad OR-Gatter (Carry-Zusammenführung) |
| **DIP-Schalter** | 2 | 4-polig, für die Eingabe von Zahl A und B |
| **LEDs** | 5 | Anzeige für $s_0, s_1, s_2, s_3$ und $c_3$ |
| **Widerstände** | 8 | $10k\Omega$ (Pull-Down für die Schalter) |
| **Widerstände** | 5 | $440\Omega$ (Vorwiderstände für LEDs) |
| **Breadboard** | 1 | Standard 830-Point Breadboard |
| **Verdrahtung** | - | 0,5mm Starrdraht (farblich sortiert) |

---

## 💡 Aufbau-Hinweise

1.  **Pull-Down Widerstände:** Da Logikgatter keine "schwebenden" (floating) Eingänge verarbeiten können, werden die $10k\Omega$ Widerstände genutzt, um die Eingänge sicher auf Masse (GND) zu ziehen, wenn die Schalter offen sind.
2.  **Signalpfad:** Das Carry-Signal wird von einer Stufe zur nächsten weitergereicht. Achte besonders auf die Verbindung vom Ausgang des ersten AND-Gatters (Bit 0) zum Eingang des nächsten Full Adders.
3.  **Kabelführung:** Verwende rechtwinklig gebogene Drähte für eine übersichtliche Fehlersuche – das Auge baut mit!

---

## 🎓 Lerneffekt

Durch den Bau dieses Addierers lernt man:
* Wie binäre Addition auf elektrischer Ebene funktioniert.
* Die Bedeutung von **Propagation Delay**: Jedes Gatter benötigt Zeit zum Schalten. Bei vielen Bits muss man warten, bis der Carry durch alle Stufen "gerippelt" ist.
* Praktisches Schaltungsdesign und Fehlersuche (Debugging) in der Digitaltechnik.

---
*Inspired by Ben Eater*
