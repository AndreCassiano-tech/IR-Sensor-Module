


# ⚡ Pure Hardware Infrared (IR) Sensor Module

## 📌 Project Overview
A standalone, non-programmable infrared proximity and obstacle detection module. This design utilizes a purely analog/mixed-signal architecture to process sensor signals and trigger external logic loads without the overhead or latency of a microcontroller.

### 📐 Technical Specifications
- **Operating Voltage:** 3.3V – 5.0V DC
- **Layer Count:** 2-Layer Board (Signal/Power Top - Unbroken GND Plane Bottom)
- **Dimensions:** 32mm x 14mm
- **Signal Output:** Active-LOW Digital Pulse (Sinks current via an open-drain/comparator stage)
- **Detection Range:** Adjustable via onboard potentiometer (Approx. 2cm – 30cm)

---

## 🎨 Circuit Layout & Visualizations

| 3D PCB Render | Schematic Capture |
| :---: | :---: |
| ![3D View](documentation/3d_render_view.png) | ![Schematic](documentation/schematic_capture.png) |

---

## 🛠️ Hardware Design Architecture & Trade-Offs

### 1. Signal Conditioning (The Comparator Circuit)
Instead of processing analog photodiode curves via firmware, this board implements an **LM358 Operational Amplifier configured as a voltage comparator. 
- **Reference Voltage:** Set via a multi-turn trimmer potentiometer to tune detection thresholds precisely.
- **Hysteresis:** Added a feedback resistor across the comparator to prevent output "chatter" or oscillation when an object is sitting right on the detection threshold boundary.

### 2. PCB Layout & Signal Integrity Choices
- **Decoupling Strategy:** Placed a `0.1µF` ceramic capacitor as physically close as possible to the VCC pin of the operational amplifier to filter high-frequency switching noise.
- **Ground Return Paths:** Dedicated the entire bottom layer to an unbroken Ground Plane to mitigate parasitic inductance and isolate the analog sensing lines from external electromagnetic interference (EMI).

---

## 🏭 Production & Bill of Materials (BOM)
All components utilize highly available **0805 Surface Mount Device (SMD)** footprints to balance space savings with ease of manual prototyping/hand-soldering.

- **Gerber Files:** Fully verified against standard design rule checks (DRC). The production-ready archive can be downloaded directly from the [Manufacturing Outputs Folder](./manufacturing_outputs).

