---
title: Heat Exchanger Design & CFD Analysis
date: 2018-04-02
label: Spring 2018
description: Designing an automotive heat exchanger in SolidWorks and evaluating its performance with a steady-state CFD analysis in ANSYS Fluent
image: '/images/heatexchanger_front.png'
featured:
timeline: Spring 2018
tools: ANSYS Fluent, SolidWorks, Excel
medias:
  - paragraph_index: '0'
    url: '/images/heatexchanger_iso.png'
    media_type: 'image'
    subtitle: 'Heat exchanger and duct geometry.'
---
# Background

The midterm project for Cooper Union's Computational Fluid Dynamics (CFD) course split the class into 4-person teams to design an automotive heat exchanger under prespecified temperature and velocity constraints. The goal of this project is to minimize the size and dry weight of the heat exchanger while maintaining an engine oil temperature drop from 350°F to 195°F maximum, while the incoming air is at a temperature of 108°F, while the oil is flowing between 3.5 gpm and 5.5 gpm, and while the vehicle is moving at 25 mph. Air is delivered to cool the engine air via a duct mounted 60 inches upstream of the proposed heat exchanger; the design of the duct aside from its inlet area is also to be designed. No constraints are placed on material compatibility or pressure drops for air or oil across the heat exchanger aside from common sense engineering assumptions in line with existing automotive heat exchangers. We performed a set of steady-state CFD simulations in tandem with design and validation hand calculations to carry out this design task.

Each team is provided with the same design limitations, performance criteria, and design goal. The assignment with all applicable rules is attached <a href="{{ '/pdfs/ME407_Midterm_Spring_2018.pdf' | relative_url }}" target="_blank">here</a>.

# Design Concept

Based on existing automotive heat exchanger designs, we elected to design a finned crossflow heat exchanger with a staggered tube bank and with both fluids unmixed. The heat exchanger tubes are made using copper and the duct is made using 6061 aluminum; the copper is chosen primarily for its high thermal conductivity, while the aluminum is chosen for its relatively low density and thermal conductivity. We neglected radiative effects in both the hand calculations and simulations based on a preliminary hand calculation confirming that radiative effects are very small compared to the forced convective effects throughout the heat exchanger. The heat exchanger duct smoothly transitions along its 60" length from the required 22" x 12" cross section to the 8" x 8" inlet area of the heat exchanger.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/heatexchanger_drawing1.png" loading="lazy" alt="Heat exchanger staggered tube arrangement">
    <img src="/images/heatexchanger_drawing2.png" loading="lazy" alt="Heat exchanger duct">
  </div>
  <em>Dimensioned design drawings of the heat exchanger (left) and duct (right). All dimensions are in inches.</em>
</div>

# Design Hand Calculations

The design hand calculations "flatten out" the heat exchanger into a long straight tube with a set of rectangular fins surrounding the tube perimeter. Each of the assumptions made in these hand calculations was validated and refined using a more detailed CFD simulation. This approach allowed us to immediately see the effects of changing geometric parameters on the overall size and dry weight of the heat exchanger, greatly simplifying the design question to a multidimensional optimization problem. We opted to use Excel to organize our calculations; Excel's Solver tool allowed for straightforward parameter optimization without the need for unnecessary simulation. Further, organizing in Excel allowed for easy visualization of how small changes in design parameters affected overall size, dry weight, air and oil flow regimes, and convective heat transfer coefficients.

![Heat exchanger simplified geometry](/images/heatexchanger_geometry.png)
*Heat exchanger simplified geometry.*

We calculated convection coefficients for oil flow inside the tube using the Dittus-Boelter equation, for air flow across the bare tube using a Nusselt number correlation for flow over a cylinder, and for air flow along the fins using a Nusselt number correlation for flow along a flat plate. With these coefficients, we created a thermal resistance network based on the simplified geometry and calculated the number of fins, heat exchanger size, and heat exchanger dry weight for a given set of geometric parameters based on the overall heat transfer coefficient and the heat transfer rate required to achieve the necessary temperature differences and mass flow rates in the air and oil streams.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/heatexchanger_thermal_circuit.png" loading="lazy" alt="Heat exchanger thermal circuit">
  </div>
  <em>Heat exchanger thermal circuit for a fin and tube segment.</em>
</div>

# CFD Simulation Setup and Mesh

We developed three CFD simulations in developing our heat exchanger design: one of the air duct to the heat exchanger, one of a single tube segment with two fins, and one with a simplified tube bank with two fins. The air duct simulation confirmed the heat exchanger entrance velocity and the pressure drop across the duct. The single tube segment simulation confirmed that the fin thickness and the distance between adjacent fins were set such that the thermal boundary layers would converge at the end of the modeled fin. The double tube segment simulation confirmed that the distance between tube rows was set such that the air from one row would not significantly thermally interact with the air the next row. This simulation also confirmed that the calculation method for determining the pressure drop for the air and oil in the design hand calculations was appropriate, accounting for the oil pressure drop across the tube bend. 

<div class="gallery-box">
  <div class="gallery_three">
    <img src="/images/heatexchanger_duct.png" loading="lazy" alt="Heat exchanger duct geometry">
    <img src="/images/heatexchanger_twofin.png" loading="lazy" alt="Heat exchanger two-fin simulation geometry">
    <img src="/images/heatexchanger_twotube.png" loading="lazy" alt="Heat exchanger tube bank simulation geometry">
  </div>
  <em>Heat exchanger simulation geometry for the duct simulation (left), the two-fin simulation (middle), and the tube bank simulation (right). Oil flows through the tube while air flows perpendicularly to the tube.</em>
</div>

The air boundaries are all modeled as symmetry boundary conditions aside from the leftmost and rightmost walls, which have mass flow inlet and pressure outlet boundary conditions, respectively. The oil in the tube is modeled similarly with one mass flow inlet and one pressure outlet boundary condition.

All simulations use the k-omega SST turbulence model; this model captures the near-wall behavior near the fins well while also capturing the fully turbulent free-stream flow in and around the heat exchanger tube bank. All simulations ran for 1,000 iterations in steady state using a pressure-based solver with the SIMPLE algorithm used for pressure/velocity coupling.

We used polyhedral meshing in ANSYS Fluent to model both the air and solid copper for each simulation. All fluid regions have five-element tall boundary layers and all solid regions have one-element tall boundary layers to properly capture conjugate heat transfer between the materials and to maintain a wall y+ below 1 at the fins and along the tube/duct length.

<div class="gallery-box">
  <div class="gallery_three">
    <img src="/images/heatexchanger_duct_mesh1.png" loading="lazy" alt="Heat exchanger duct overall mesh">
    <img src="/images/heatexchanger_twofin_mesh1.png" loading="lazy" alt="Heat exchanger two-fin model overall mesh">
    <img src="/images/heatexchanger_twotube_mesh1.png" loading="lazy" alt="Heat exchanger tube bank model overall mesh">
    <img src="/images/heatexchanger_duct_mesh2.png" loading="lazy" alt="Heat exchanger duct mesh cross section">
    <img src="/images/heatexchanger_twofin_mesh2.png" loading="lazy" alt="Heat exchanger two-fin model mesh cross section">
    <img src="/images/heatexchanger_twotube_mesh2.png" loading="lazy" alt="Heat exchanger tube bank model mesh cross section">
  </div>
  <em>Heat exchanger simulation mesh for the duct simulation (upper/lower left), the two-fin simulation (upper/lower middle), and the tube bank simulation (upper/lower right).</em>
</div>

# Results

Our model results show close agreement with the design hand calculations (maximum ~15% difference) and prove that the assumptions made in these calculations were justified. Results indicate that an 8" x 8" x 8" heat exchanger weighing 24.33 lbs is sufficient to cool the engine oil to the required 195°F criterion while still maintaining a realistic oil and air pressure drop and maintaining a feasible, manufacturable design.

<div class="gallery-box">
  <div class="gallery_three">
    <img src="/images/heatexchanger_duct_comparison.png" loading="lazy" alt="Heat exchanger duct hand calculation comparison">
    <img src="/images/heatexchanger_twofin_comparison.png" loading="lazy" alt="Heat exchanger two-fin simulation hand calculation comparison">
    <img src="/images/heatexchanger_twotube_comparison.png" loading="lazy" alt="Heat exchanger tube bank simulation hand calculation comparison">
  </div>
  <em>Comparison of design hand calculation results to duct simulation (left), two-fin simulation (middle), and tube bank simulation (right).</em>
</div>

<br />

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/heatexchanger_duct_velocity.png" loading="lazy" alt="Heat exchanger duct velocity streamlines">
    <img src="/images/heatexchanger_duct_pressure.png" loading="lazy" alt="Heat exchanger duct pressure contours">
  </div>
  <em>Summary of duct simulation velocity streamline results (left) and pressure contour results (right).</em>
</div>

<br />

<div class="gallery-box">
  <div class="gallery_three">
    <img src="/images/heatexchanger_twofin_velocity.png" loading="lazy" alt="Heat exchanger two fin velocity streamlines">
    <img src="/images/heatexchanger_twofin_temp1.png" loading="lazy" alt="Heat exchanger two fin temperature contours">
    <img src="/images/heatexchanger_twofin_temp2.png" loading="lazy" alt="Heat exchanger two fin temperature contours">
    <img src="/images/heatexchanger_twofin_oil_pressure.png" loading="lazy" alt="Heat exchanger two fin oil pressure contours">
    <img src="/images/heatexchanger_twofin_air_pressure.png" loading="lazy" alt="Heat exchanger two fin air pressure contours">
  </div>
  <em>Summary of two-fin simulation velocity streamline results (upper left), temperature contour results (upper middle/right), oil pressure contour results (lower left), and air pressure contour results (lower middle).</em>
</div>

<br />

<div class="gallery-box">
  <div class="gallery_three">
    <img src="/images/heatexchanger_twotube_oil_velocity.png" loading="lazy" alt="Heat exchanger tube bank oil velocity streamlines">
    <img src="/images/heatexchanger_twotube_air_velocity.png" loading="lazy" alt="Heat exchanger tube bank air velocity streamlines">
    <img src="/images/heatexchanger_twotube_temp1.png" loading="lazy" alt="Heat exchanger tube bank temperature contours">
    <img src="/images/heatexchanger_twotube_temp2.png" loading="lazy" alt="Heat exchanger tube bank temperature contours">
    <img src="/images/heatexchanger_twotube_oil_pressure.png" loading="lazy" alt="Heat exchanger tube bank oil velocity streamlines">
    <img src="/images/heatexchanger_twotube_air_pressure.png" loading="lazy" alt="Heat exchanger tube bank air velocity streamlines">
  </div>
  <em>Summary of tube bank simulation oil velocity streamline results (upper left), air velocity streamline results (upper right), temperature contour results (upper right/lower left), oil pressure contour results (lower middle), and air pressure contour results (lower right).</em>
</div>

A 55-page report further detailing the operating metrics, design hand calculations, all CFD simulations, and fully dimensioned design drawings can be found <a href="{{ '/pdfs/ME407_Midterm_Report.pdf' | relative_url }}" target="_blank">here</a>.
