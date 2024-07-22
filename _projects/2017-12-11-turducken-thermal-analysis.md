---
title: Turducken Thermal Design and Analysis
date: 2017-12-11
label: Fall 2017
description: Designing a turducken cooking system in SolidWorks and evaluating its performance with a transient thermal analysis in ANSYS Workbench
image: '/images/turducken_mesh_iso.png'
featured: true
timeline: Fall 2017
tools: ANSYS Workbench, Altair Hypermesh, SolidWorks, MATLAB
medias:
  - paragraph_index: '0'
    url: '/images/turducken_cross_section.png'
    media_type: 'image'
    subtitle: 'Turducken geometry: turkey layer in orange, duck/chicken layer in gray, and stuffing layer in blue.'
  - paragraph_index: '2'
    url: '/images/turducken_mesh_side.png'
    media_type: 'image'
    subtitle: 'Turducken mesh.'
  - paragraph_index: '8'
    url: '/videos/turducken_animation.mp4'
    media_type: 'video'
    subtitle: 'Turducken heating animation.'
---
# Background

The final project for Cooper Union's Introduction to Computer Aided Engineering (CAE) course split the class into 4-person teams to analyze the cooking process for a turducken using a convection oven and two resistive heating skewers. The turducken consists of 3 layers: an outer layer of only turkey, a middle layer consisting of a homogeneous mixture of duck and chicken, and an inner layer of a team-selected stuffing. The goal of this project is to minimize the amount of time taken to "fully cook" the turducken (minimum temperature of 185°F) while also minimizing the percentage of "burnt" turducken (minimum temperature of 265°F). We performed a transient thermal analysis on the turducken using ANSYS Workbench and validated our results with a simplified hand calculation.

Each team is provided with the same turducken geometry, restrictions on the temperature criteria, and design limitations for the skewers and oven. The assignment with all applicable rules is attached <a href="{{ '/pdfs/ME408_Final_Fall_2017.pdf' | relative_url }}" target="_blank">here</a>.

# Setup and Mesh

Our team used a simple pointed rod design for the skewers, placing them through the thickest segments of the turducken as these were the areas with the highest thermal capacitance. Using the 2006 ASHRAE Refrigeration Handbook, we determined the relevant thermal conductivity, density, and specific heat for each material as a function of temperature, weighting homogeneous mixtures gravimetrically for specific heat and volumetrically for thermal conductivity and density. We additionally accounted for the changes in these properties as the water in each material evaporated out and as each material burned.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/turducken_side.png" loading="lazy" alt="Turducken side view with skewers">
    <img src="/images/turducken_rear.png" loading="lazy" alt="Turducken rear view with skewers">
  </div>
  <em>Turducken with skewers side and rear views.</em>
</div>

We split the turducken in half along the turducken vertical midplane due to geometric and thermal symmetry in the analysis, significantly reducing our mesh size and solve time. All convection coefficients and emissive properties were approximated from online research based on similar studies in standard convection ovens as physical experimentation and CFD methods were outside the scope of this analysis.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/turducken_bcs.png" loading="lazy" alt="Turducken boundary conditions">
  </div>
  <em>Turducken boundary conditions.</em>
</div>

We used Altair Hypermesh to slice the stuffing, ducken, wing, and skewer to allow for mapped hexahedral meshing where possible. Because the turkey is not as easily mappable, we opted to use a hexcore mesh primarily for mesh space efficiency. Where hexahedral elements could not be used, we used smaller tetrahedral elements, notably at locations where we expected higher temperature gradients (e.g., around the skewer). The mesh had a total element count of approximately 495,000. All elements were element type SOLID70.

# Validation

To validate the results obtained by the model, we created an equivalent transient thermal RC circuit to capture the rise in temperature at nodes across the turducken. The model treats the turducken as a set of concentric spheres, lumping the resistive and capacitive effects for each layer. The skewer is treated as a current source that is turned on and off at specific times in the analysis. The resulting coupled ODEs are assembled in MATLAB and are solved concurrently using Forward Euler numerical methods.

![Turducken Thermal Circuit](/images/turducken_thermal_circuit.png)
*Turducken thermal circuit.*

Hand calculation results indicate that the skewers should remain on for approximately 4.25 hours before being shut off to minimize the percentage of burnt turducken while drastically reducing cooking time.

# Results

Our model results show close agreement with the hand calculations (maximum ~20% difference). Results indicate that, if the skewers are left on for 4.25 hours and if the turducken is left in the oven for 6.25 hours, the turducken is only 39% burnt. Compared to a similar analysis without the skewers, the turducken with skewers is 20% less burnt and needs about 6 fewer hours in the oven.

![Hand calculation heating results](/images/turducken_hand_calc_and_analysis.png)
*Hand calculation results compared to analysis results: solid lines represent ANSYS simulation results, and dashed lines represent hand calculation results.*

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/turducken_hour1.png" loading="lazy" alt="Turducken temperature after 1 hour in the oven">
    <img src="/images/turducken_hour3.png" loading="lazy" alt="Turducken temperature after 3 hours in the oven">
    <img src="/images/turducken_hour5.png" loading="lazy" alt="Turducken temperature after 5 hours in the oven">
    <img src="/images/turducken_hour6.png" loading="lazy" alt="Turducken temperature after 6.25 hours in the oven">
  </div>
  <em>Turducken temperature after 1 hour (upper left), 3 hours (upper right), 5 hours (lower left), and 6.25 hours (lower right) in the oven.</em>
</div>

A 52-page report further detailing the hand calculation, model, skewer design, and cooking instructions can be found <a href="{{ '/pdfs/ME408_Final_Report.pdf' | relative_url }}" target="_blank">here</a>.
