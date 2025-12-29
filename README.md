# Anti-Z-Wobble-Flexures
Low cost SOTA performance 3d printable flexure based substitute for Oldham couplings.

Onshape project focussing on solving z-axis misalignment and wobble induced printing artifacts using flexures.

---
Z-wobble in 3D printing is a mechanical issue where the Z-axis (vertical) movement isn't perfectly straight, 
causing the nozzle to shift slightly sideways, resulting in visible, repeating horizontal lines or ripples 
(Z-banding) on the print's surface. It's a hardware problem, often from bent lead screws, misaligned couplers,
and leads to inconsistent layer stacking. 

The approach to solving z-wobble and related artifacts is by releasing the x and y degrees of freedom at 
the interface between the T8-nut and the printer bed. (Same as any anti-wobble nut, oldham couplings, WobbleX) 
These DOFs are over-constrained by the linear rails AND the threaded rod. 
This project utilizes [Flexures](https://en.wikipedia.org/wiki/Flexure) to achieve this constraint relaxation. 
See [FACT](https://en.wikipedia.org/wiki/Freedom_and_constraint_topologies) for more info on design considerations.

---
## Quick Overview

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

| Design | Purpose | Onshape Link |
| :--- | :--- | :--- |
| **Design A: [Parallelogram]** | [Low x,y stiffness] | [Open Live Model 🔗](https://cad.onshape.com/documents/e9f5f3ec017cd79d059d23d6/w/ac5a599820a5beecc4798aae/e/dd3290a3d811bc061c931160?configuration=default&renderMode=0&uiState=69528658e2474bc8591230e6) |
| **Design B: [Planar]** | [Flat profile] | [Open Live Model 🔗](https://cad.onshape.com/documents/95f8fcc605a67b3147b08d67/w/e3557ddfdb1231eb4b031d51/e/2aff83f88191c0ca42ad76a6?renderMode=0&uiState=69528a697de4240c3342bd8b) |

---

## 1. Design A: [Parallelogram]
[Recommended Design, well suited for 3d printing and dimensions are similar to oldham coupling.]
<table border="0" align="center">
  <tr>
    <td>
      <p align="center"><b>Design A: Standard</b></p>
      <img src="Design A Parallelogram/Images/Parallelogram-Z-Flexure.PNG" width="400">
    </td>
    <td>
      <p align="center"><b>Design A: Reinforced Leaf Springs</b></p>
      <img src="Design A Parallelogram/Images/Parallelogram-Z-Flexure-Reinforced.PNG" width="400">
    </td>
  </tr>
</table>


### Key Specifications
* **Standard Dimensions:** 28.7x28.7x37.5mm (without bolts)
* **Reinforced Dimensions:** 28.7x28.7x42.833mm (without bolts) (reinforced leaf spring version)
* **Hardware Required:** BOM: M3x8mm 8 times, M2.5x8mm 16 times, Threaded T8-Nut
* **Main Features:**
	**Pros**: Easily achieves low x-y stiffness while maintaining high stiffness in other DOFs. 
		Easier printing, and easier to tune stiffness than design B.   
	**Cons**: Z-deflection becomes relational to x-y deflections (see figure) & "Tricky" assembly

<p align="center">
  <img src="Design A Parallelogram/Images/AntiWobbleDeflectionGraph_Shaded.jpg" width="600" title="Deflection in Z as product of deflection in x,y">
</p>



<table border="0" align="center">
  <tr>
    <td>
      <p align="center"><b>Design A: Standard</b></p>
      <img src="Design A Parallelogram/Images/Parallelogram-Z-Flexure-Section.PNG" width="300">
    </td>
    <td>
      <p align="center"><b>Design A: Reinforced Leaf Springs</b></p>
      <img src="Design A Parallelogram/Images/Parallelogram-Z-Flexure-Reinforced-Section.PNG" width="300">
    </td>
  </tr>
</table>

**Note: Highly recommended to use Torx for any bolts below M3 because hex-bolts start stripping easily.**

---

## 2. Design B: [Planar]
[Experimentation with linear planar motion stages. This design works but is more difficult to print, but the design is well suited to be adapted for a CNC based solution can easily be machined.]

<p align="center">
  <img src="Design B Planar/Images/Planar-Z-Flexure.PNG" width="600" title="Deflection in Z as product of deflection in x,y">
</p>

### Key Specifications
* **Dimensions:** 52x52x12.5mm (without bolts)  
* **Hardware Required:** M3x8mm 8 times, M3x12mm 4 times, Threaded T8-Nut   
* **Main Features:**   
  	**Pros**: Very simple, symetric design, design structure well suited CNC machining.  
	**Cons**: Lower relative stiffness, akward shape, harder to print.  

  
<p align="center">
  <img src="Design B Planar/Images/Planar-Z-Flexure-Section.PNG" width="600" title="Deflection in Z as product of deflection in x,y">
</p>

---

### Onshape Workflow
To modify this design:
1. Open [Design A](https://cad.onshape.com/documents/e9f5f3ec017cd79d059d23d6/w/ac5a599820a5beecc4798aae/e/dd3290a3d811bc061c931160?configuration=default&renderMode=0&uiState=69528658e2474bc8591230e6) or [Design B](https://cad.onshape.com/documents/95f8fcc605a67b3147b08d67/w/e3557ddfdb1231eb4b031d51/e/2aff83f88191c0ca42ad76a6?renderMode=0&uiState=69528a697de4240c3342bd8b).
2. Click **"Make a Copy"** (requires a free Onshape account) to edit.

---

## ⚖️ License

This project is licensed under the **Open Community License (OCL)**.

* **Personal Use:** You are free to print, build, and modify these designs for your own use.
* **Internal Business Use:** You may use these designs within your company (e.g., as tools on a production line).
* **Commercial Restriction:** You may **not** sell the 3D files or physical 3D-printed versions of these designs for profit without explicit permission from the author.
* **Attribution:** Any redistribution must include credit to the original author.

[View the full OCL terms here](https://github.com/OpenCommunityLicence/OpenCommunityLicence)

---
