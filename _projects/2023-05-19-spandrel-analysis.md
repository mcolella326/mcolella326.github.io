---
title: Thermal Performance of Spandrel Assemblies in Glazed Wall Systems
date: 2023-05-19
label: Spring 2023
description: Outlining an accurate and repeatable procedure for assessing spandrel panel system thermal performance using steady-state CFD analyses
image: '/images/pankow_cover.png'
featured: true
timeline: Spring 2023
tools: StarCCM+, THERM, SolidWorks, Design of Experiments
medias:
---
# Background

This research project funded by the <a href="https://www.pankowfoundation.org/" target="_blank">Charles Pankow Foundation</a> is a joint effort from three firms (Simpson Gumpertz & Heger, Morrison Hershfield, and RDH) to develop a consistent simulation methodology for evaluating the thermal performance of spandrels in glazing systems. We use 2D and 3D simulations, in addition to experimental testing with the help of Oak Ridge National Laboratory, to study the 2D and 3D heat flow effects that are often ignored in current calculation methods.

A spandrel is a pane-like area between the head of a window on one level and the sill of the window immediadely above. Typical spandrel assemblies consist of an intermediate panel, insulation, and an interior backpan.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_spandrel_diagram.png" loading="lazy" alt="Spandrel diagram">
    <img src="/images/pankow_spandrel.png" loading="lazy" alt="Spandrel assembly">
  </div>
  <em>Typical spandrel front view (left) and section view (right).</em>
</div>

My role in this phase of the project consisted of performing 2D FEA and 3D CFD simulations of vented and sealed spandrel assemblies under various exterior wind speed conditions to compare local temperature results and overall thermal performance results. I additionally assisted in developing a laboratory testing program to validate these simulations, assessing critical locations for thermocouple placement and using Design of Experiments techniques to determine a set of variants to be tested in future phases.

# CFD Simulation and Results

One of the objectives of this study was to explore the effect of airflow within the spandrel panel on the thermal performance of the assembly. In a set of CFD simulations, I investigated the impact of vent openings and external airflow speed on spandrel thermal performance. The simulation is based on a typical stick-built curtain wall system; this system has the most direct airflow path between the spandrel air cavity and the exterior relative to unitized assemblies and would most clearly demonstrate the impact of airflow on thermal performance.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_cfd_geometry.png" loading="lazy" alt="CFD gemetry with elements labeled">
  </div>
  <em>CFD geometry with elements labeled.</em>
</div>

In each of the four simulations performed, I varied the placement of vent holes in the spandel cavity and the magnitude of the exterior wind speed. The wind speeds are based on either the maximum wind speed the fans could produce in the experimental setup or the average wind speed prescribed in current calculation methods. I used the k-epsilon turbulence model for each simulation.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_cfd_bcs.png" loading="lazy" alt="CFD simulation boundary conditions">
  </div>
  <em>CFD simulation boundary conditions.</em>
</div>

<br />

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_cfd_mesh.png" loading="lazy" alt="CFD simulation mesh">
  </div>
  <em>CFD simulation fluid mesh for sealed and ventilated conditions (solid mesh hidden for clarity).</em>
</div>

Airflow velocity results indicate that high exterior air velocity would result in higher average air velocity in the spandrel and increased penetration of exterior air into the spandrel cavity for ventilated cases. For sealed cases, air pressure differences do not contribute to the air velocity variations within the air cavity; the increased air velocity adjacent to the vertical wlals in the cavity is caused by internal natural convection driven by surface temperatures. The internal convection is greater for the high velocity case due to the colder exterior surface temperature generated from the higher exterior air velocity.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_velocity.png" loading="lazy" alt="CFD simulation velocity results">
  </div>
  <em>CFD simulation velocity results.</em>
</div>

Temperature results indicate that, although there are discernible temperature differences at the lower vent openings, the temperature differences dissipate away from the openings, similar to the velocity results. The average temperature difference between the ventilated and sealed cases is negligible when averaged across the entire interior surface.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_backpan1.png" loading="lazy" alt="CFD simulation temperature results (low wind speed)">
    <img src="/images/pankow_backpan2.png" loading="lazy" alt="CFD simulation temperature results (high wind speed)">
    <img src="/images/pankow_section1.png" loading="lazy" alt="CFD simulation temperature section results (low wind speed)">
    <img src="/images/pankow_section2.png" loading="lazy" alt="CFD simulation temperature section results (high wind speed)">
  </div>
  <em>CFD simulation temperature results for low wind velocity (left) and high wind velocity (right).</em>
</div>

# FEA Simulation and Comparison to CFD

I additionally created a 2D FEA model of the same geometry using THERM, free thermal analysis software produced by Lawrence Berkeley National Laboratory. This model matches the 3D CFD model in terms of geometry, simulation extents, solid material thermal conductivities, and boundary conditions. The most notable difference between models is that all air layers in the 2D FEA simulation use an air cavity solid material, while the 3D CFD simulation accounts for air movement with turbulence parameters.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_therm_geometry.png" loading="lazy" alt="FEA simulation geometry">
    <img src="/images/pankow_therm_bcs.png" loading="lazy" alt="FEA simulation boundary conditions">
  </div>
  <em>FEA simulation geometry (left) and boundary conditions (right).</em>
</div>

To compare results between CFD and FEA, I probed temperature results along the spandrel cavity midplane for both simulations at specific points of interest. A primary reason for differences at the center of panel section (where 3D heat transfer effects are reduced) is that the air volume properties in 2D FEA thermal simulations are diffusion-based, while the air volume properties in 3D CFD simulations account for advection. Exterior air velocity is used to derive a uniform film coefficient at the exterior surface of a 2D FEA thermal simulation. However, 2D FEA thermal simulations do not account for temperature changes due to steady-state mass flow through the vent openings whereas this is accounted for in 3D CFD simulations.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_cfd_probes.png" loading="lazy" alt="CFD temperature probe locations">
    <img src="/images/pankow_therm_probes.png" loading="lazy" alt="FEA temperature probe locations">
  </div>
  <em>Temperature probe locations for CFD simulation (left) and FEA simulation (right).</em>
</div>

<br />

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_probe_comparison.png" loading="lazy" alt="Temperature probe comparison between CFD and FEA">
  </div>
  <em>Temperature probe comparison between CFD and FEA.</em>
</div>

I additionally derived overall heat transfer coefficient (U-factor) results from both the CFD and FEA simulations, demonstrating approximate equivalence between simulation methods.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_factors.png" loading="lazy" alt="U-factor comparison between CFD and FEA">
  </div>
  <em>U-factor comparison between CFD and FEA.</em>
</div>

# Experimental Testing Preparation

The objective of laboratory testing is to validate simulation methods against measured data to develop a set of simulation guidelines to evaluate spandrel assembly thermal performance. The laboratory tests are designed to cover multiple systems and configurations that capture conditions typically found in the field, including the impacts of panel size, adjacent assemblies, intermediate floor attachments, spandrel construction, and airflow around the spandrel assembly.

The proposed test articles used consist of curtain wall or window wall systems that are divided into 5 panels. These articles include 4 spandel panel types, 1 vision panel, and an adjacent insulated steel-frame wall assembly. The tests will be carried out using hot box equipment capable of testing large articles at steady-state conditions.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_panel.png" loading="lazy" alt="Proposed test article">
    <img src="/images/pankow_hotbox.png" loading="lazy" alt="Laboratory hot box testing rig">
  </div>
  <em>Proposed test article (left) and laboratory hot box testing rig (right).</em>
</div>

Temperatures at critical locations will be measured when the test articles are subjected to a temperature difference at steady-state conditions in the hot box testing rig. We will measure surface temperatures, ambient air temperatures, and airflow around the test article under natural convection conditions on the interior and winter wind conditions on the exterior.

Up to 200 thermocouples, sensitive to 0.18°F (0.1°C), are to be installed at critical locations within the spandrel panel. The sensors will record measurements at frequent intervals (e.g., 5 to 15 minutes) to determine when a steady state is achieved.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/pankow_thermocouples.png" loading="lazy" alt="Proposed thermocouple locations on panel section">
  </div>
  <em>Proposed thermocouple locations on panel section.</em>
</div>

A 156-page paper published by the Charles Pankow Foundation further detailing the current state of practice for evaluating spandel assembly thermal performance, current relevant codes and standards, industry surveys for how spandrel assemblies are currently used in industry, and the laboratory testing guideline can be found <a href="https://www.pankowfoundation.org/site/assets/files/2320/04-22_thermal_performance_of_spandrel_assemblies_in_glazed_wall_systems-1.pdf" target="_blank">here</a>.
