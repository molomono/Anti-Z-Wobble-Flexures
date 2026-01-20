# Anti-Z-Wobble Flexures
Low cost SOTA performance 3d printable flexure based drop-in substitute for Oldham couplings.   
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
	- Parametric Design So the dimensions of the model can easily be changed to better fit the users requirements. (see Onshape Workflow below)

Main benefits:   
	- Fixes minor misalignments, (releasing overconstrained Z-motion system)   
	- Flexure, thus no friction motion, therefore low hysteresis. (State of the Art performance for T8 threaded z-axis printers)   
	- Exceptionally low cost, (3D printed designs, practically free except for a few M2.5/M3 screws)   

Main downside:
	- Use in heated environments will require apropriate choice of material.

---

| Design | Key property | Onshape Link |
| :--- | :--- | :--- |
| **Design A V2: [Parallelogram]** | [Low x,y stiffness] | [Open Live Model 🔗](https://cad.onshape.com/documents/e9f5f3ec017cd79d059d23d6/w/ac5a599820a5beecc4798aae/e/dd3290a3d811bc061c931160?configuration=default&renderMode=0&uiState=69528658e2474bc8591230e6) |
| **Design A V3: [Parallelogram]** | [Stiffer Z DoFs] | [Open Live Model 🔗](https://cad.onshape.com/documents/0bdb8cc5919d48aaf7c68062/w/57636940a288332a187afe87/e/9ee4d49a4399172ee17dd28a) |
| **Design B: [Planar]** | [Flat profile] | [Open Live Model 🔗](https://cad.onshape.com/documents/95f8fcc605a67b3147b08d67/w/e3557ddfdb1231eb4b031d51/e/2aff83f88191c0ca42ad76a6?renderMode=0&uiState=69528a697de4240c3342bd8b) |

---

## 1. Design A: [Parallelogram]
[V3 is the Recommended Design, well suited for 3d printing and dimensions are similar to oldham coupling.]

<p align="center">
  <img src="Design A V3/Images/V3-General.PNG" width="600" title="Deflection in Z as product of deflection in x,y">
</p>

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
* **V3 Dimensions:** 38.8x38.8x39.0mm (without bolts) (V3 reinforced leaf spring version)
* **Hardware Required:** BOM: M3x8mm 8 times, M2.5x8mm 16 times (V3 uses 24), Threaded T8-Nut
* **Main Features:**  
	**Pros**: Easily achieves low x-y stiffness while maintaining high stiffness in other DOFs. 
		Easier printing, and stiffness tuning than design B.   
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

## Notes on print-settings
### Design A:
* I used PLA but PLA-CF/-GF might improve performance due to the print orietnation of the springs.
* Leaf springs must be printed flat with the reinforcements pointed up. Make sure that the unreinforced part of the springs is 100% considered bottom/top shell.
* Using rectilinear infill makes for good internal reinforcement structure. 30% is sufficient.
* Use 3-4 perimeter walls and 30% infill on the other printed boddies.
* Over-extruding the first layer is fine for functionality of this part, underextruding WILL cause issues.

### Design B:
* Make sure the seams do not align near the connection point between spring and body.
* Make sure the nozzle diameter ensures there are at least 2 walls in each spring.
* If the above requirements aren't met the springs can disconnect from the body.

---

### Onshape Workflow
To modify this design:
1. Open [Parallelogram Design](https://cad.onshape.com/documents/e9f5f3ec017cd79d059d23d6/w/ac5a599820a5beecc4798aae/e/dd3290a3d811bc061c931160?configuration=default&renderMode=0&uiState=69528658e2474bc8591230e6) or [Planar Design](https://cad.onshape.com/documents/95f8fcc605a67b3147b08d67/w/e3557ddfdb1231eb4b031d51/e/2aff83f88191c0ca42ad76a6?renderMode=0&uiState=69528a697de4240c3342bd8b).
2. Click **"Make a Copy"** (requires a free Onshape account) to edit.
3. The variable table can be opened on the right from which dimensions of the model can be altered to better suit your needs.

---

## ⚖️ License

This project is licensed under the **Open Community License (OCL)**.
[View the full OCL terms here](https://github.com/OpenCommunityLicence/OpenCommunityLicence)

---
