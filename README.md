# Anti-Z-Wobble-Flexures
Low cost SOTA performance 3d printable flexure based substitute for Oldham couplings.

Onshape project focussing on solving z-axis misalignment and wobble induced printing artifacts using flexures.

---
Z-wobble in 3D printing is a mechanical issue where the Z-axis (vertical) movement isn't perfectly straight, 
causing the nozzle to shift slightly sideways, resulting in visible, repeating horizontal lines or ripples 
(Z-banding) on the print's surface. It's a hardware problem, often from bent lead screws, misaligned couplers,
and leads to inconsistent layer stacking. 

A consequence of this wobble is the varying radial forces between the lead screw and the nut.
This results in uncertain friction between the screw and nut threads. These uncertainties directly impact 
performance negatively in a broad sense, even when using velocity/position-controlled actuators. (steppers) 
In severe cases, it can cause binding/skipping of the z-axis, especially with more rigid printer builds.

The approach to solving z-wobble and related artifacts is by releasing the x and y degrees of freedom at 
the interface between the T8-nut and the printer bed. (Same as any anti-wobble nut, oldham couplings, WobbleX) 
These DOFs are over-constrained by the linear rails AND the threaded rod. 
This project utilizes [Flexures](https://en.wikipedia.org/wiki/Flexure) to achieve this constraint relaxation. 
See [FACT](https://en.wikipedia.org/wiki/Freedom_and_constraint_topologies) for more info on design considerations.

Two primary designs, sharing common metrics for performance.
	- High relative stiffness between z and x-y axes, 
		- High stiffness in z axis. Flexure must easily support the bed under fast accelrations.
		- Low stiffness in x y axes.
	- High resistance to tortion around z.

Main benefits:
	- Fixes minor misalignments, (releasing overconstrained Z-motion system)
	- Flexure, thus no friction motion, therefore low hysteresis. (State of the Art performance for T8 threaded z-axis printers)
	- Exceptionally low cost, (3D printed designs, practically free except for a few M2.5/M3 screws) 

Main downside:
	- Use in heated enviroments will require apropriate choice of material.

---

## Quick Navigation

| Design | Purpose | Onshape Link |
| :--- | :--- | :--- |
| **Design A: [Parallelogram]** | [Low x,y stiffness] | [Open Live Model 🔗](https://cad.onshape.com/documents/e9f5f3ec017cd79d059d23d6/w/ac5a599820a5beecc4798aae/e/dd3290a3d811bc061c931160?configuration=default&renderMode=0&uiState=69528658e2474bc8591230e6) |
| **Design B: [Planar]** | [Flat profile] | [Open Live Model 🔗](https://cad.onshape.com/documents/95f8fcc605a67b3147b08d67/w/e3557ddfdb1231eb4b031d51/e/2aff83f88191c0ca42ad76a6?renderMode=0&uiState=69528a697de4240c3342bd8b) |

---

## 1. Design A: [Parallelogram]
[Recommended Design, well suited for 3d printing and dimensions are similar to oldham coupling.]

### Key Specifications
* **Standard Dimensions:** 28.7x28.7x37.5mm (without bolts)
* **Reinforced Dimensions:** 28.7x28.7x42.833mm (without bolts) (reinforced leaf spring version)
* **Hardware Required:** BOM: M3x8mm 8 times, M2.5x8mm 16 times, Threaded T8-Nut
* **Main Features:**
	**Pros**: Easily achieves low x-y stiffness while maintaining high stiffness in other DOFs. 
		Easier printing, and easier to tune stiffness than design B.   
	**Cons**: Z-deflection becomes relational to x-y deflections (see figure) & "Tricky" assembly

Notes: Highly recommended to use Torx for any bolts below M3 because hex-bolts start stripping easily.
---

## 2. Design B: [Planar]
[Experimentation with linear planar motion stages. This design works but is more difficult to print.]

### Key Specifications
* **Dimensions:** 52x52x12.5mm (without bolts)
* **Hardware Required:** M3x8mm 8 times, M3x12mm 4 times, Threaded T8-Nut
* **Main Features:**
  	**Pros**: Very simple, symetric design.    
	**Cons**: Lower relative stiffness, akward shape, harder to print.
---

### Onshape Workflow
To modify this design:
1. Open [Design A](https://cad.onshape.com/documents/e9f5f3ec017cd79d059d23d6/w/ac5a599820a5beecc4798aae/e/dd3290a3d811bc061c931160?configuration=default&renderMode=0&uiState=69528658e2474bc8591230e6) or [Design B](https://cad.onshape.com/documents/95f8fcc605a67b3147b08d67/w/e3557ddfdb1231eb4b031d51/e/2aff83f88191c0ca42ad76a6?renderMode=0&uiState=69528a697de4240c3342bd8b).
2. Click **"Make a Copy"** (requires a free Onshape account) to edit.

## 🛠 Manufacturing Instructions

### 3D Printing Recommended Settings
* **Material:** [e.g., PETG or PLA+]
* **Perimeters/Wall Loops:** 3 minimum
* **Infill:** 15-25% Gyroid
* **Supports:** [e.g., Required for Design A / Not required for Design B]

### Assembly Guide
1. [Step 1]
2. [Step 2]
> **Note:** Detailed assembly photos can be found in the `/Docs` folder of this repository.

---

## 📂 Repository Structure
* `/Design_A`: Static exports (STEP/STL) for the heavy-duty version.
* `/Design_B`: Static exports (STEP/STL) for the lightweight version.
* `/Common`: Shared parts used in both designs.
* `/Docs`: Assembly diagrams and high-res photos.

---

## ⚖️ License
This project is licensed under the **[Insert License Name, e.g., CERN-OHL-S v2 or CC BY-SA 4.0]**.
- **Commercial use:** [Allowed/Disallowed]
- **Attribution:** Required
- **Share Alike:** Required

---

## Contact & Contribution
If you have suggestions or find an issue, please open an **Issue** or submit a **Pull Request**. 
Designed by **[Your Name/Handle]**.
