---
title: Measuring the Traction Limits and Suspension Forces of a Formula SAE Racecar
date: 2018-05-04
label: Spring 2018
description: Using traction circles and onbard data acquisition systems to compare overall vehicle performance and to better characterize the suspension system of a Formula SAE-style racecar
image: '/images/traction_overall.png'
featured:
timeline: Spring 2018
tools: Data acquisition system with linear potentiometers and accelerometers, SolidWorks, MATLAB
medias:
---
# Background

The goal of this project was to use an onboard data acquisition system to better determine the loading distribution in the Cooper Union Formula SAE racecar suspension system throughout a typical autocross event. Each corner of the vehicle was equipped with a coilover-linear potentiometer system; the force exerted on each suspension member was determined by using real-time displacement data in conjunction with the spring constant and damper coefficient for each coilover. Using these suspension forces, we determined the force exerted on each tire and used this value as a baseline to improve suspension system effectiveness. Additionally, a traction circle (a plot showing the extents of lateral and longitudinal acceleration of the vehicle throughout the autocross event) was generated for a set of drivers and was used to identify weak areas among drivers and to compare actual vehicle performance relative to design constraints.

# Project Description

We characterized the suspension performance of the 2018 Cooper Motorsports FSAE vehicle under accelerating, braking, and cornering conditions by placing linear potentiometers alongside the coilover shocks of the suspension system and recording their deflections during a test autocross event. These deflections were used to calculate the movement of the suspension system. Using known spring and damping coefficients, we calculated the force through the spring-damper system, which can then be used to calculate the weight on the tires. Understanding these loads is essential to minimize the weight of the suspension system. Furthermore, understanding how loads are distributed throughout the suspension system can help with structural integrity and make suspension theory easier to apply for future vehicles.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/traction_coilovers.png" loading="lazy" alt="Vehicle coilover locations">
  </div>
  <em>2018 Cooper Motorsports FSAE vehicle coilover shock locations (highlighted in orange).</em>
</div>

The coilover model used already had a fixed specification for the spring constant. The damper coefficient was determined via manufacturer damper curves.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/traction_damper.png" loading="lazy" alt="Shock damper curves">
  </div>
  <em>Coilover shock damper curve.</em>
</div>

# Experimental Setup

A set of PZ-12-A-75P linear potentiometers with a 75mm stroke was used to determine the forces in the suspension system. An AiM Evo 4 data logger with an onboard accelerometer and GPS and a sampling rate of 10 Hz was used to acquire traction circle data.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/traction_front_mounting.png" loading="lazy" alt="Linear potentiometer front shock mounting">
    <img src="/images/traction_rear_mounting.png" loading="lazy" alt="Linear potentiometer rear shock mounting">
  </div>
  <em>Linear potentional front (left) and rear (right) coilover shock mounting (highlighted in orange).</em>
</div>

<br />

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/traction_logger.png" loading="lazy" alt="Linear potentiometer data logger mounting">
  </div>
  <em>Data logger mounting (highlighted in orange).</em>
</div>

Each linear potentiometer was calibrated beforehand by supplying the potentiometers with a fixed voltage and recording the voltage output at set extension lengths under both lengthening and shortening events to account for hysteresis. Calibration results and error bars indicated reliable and repeatable behavior without any discernible hysteresis.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/traction_calibration_setup.png" loading="lazy" alt="Linear potentiometer calibration setup">
  </div>
  <em>Linear potentiometer calibration setup.</em>
</div>

<br />

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/traction_calibration_results.png" loading="lazy" alt="Linear potentiometer calibration results">
    <img src="/images/traction_calibration_error.png" loading="lazy" alt="Linear potentiometer calibration error bars">
  </div>
  <em>Linear potentional calibration results (left) and error bars (right).</em>
</div>

# Results

The data logger recorded data for five different drivers on an autocross, acceleration, and skidpad course. Acceleration data recorded from the autocross course was used to produce traction circles for the two drivers who drove that course. A comparison between the two drivers' traction circles indicates that, while the two drivers had similar lateral accelerations, Driver One was capable of achieving higher longitudinal accelerations. This analysis suggest that Driver Two is not at the limits of the car's longitudinal acceleration and as room for improvement in the autocross event.

<div class="gallery-box">
  <div class="gallery_three">
    <img src="/images/traction_driver1.png" loading="lazy" alt="Traction circle for Driver One">
    <img src="/images/traction_driver2.png" loading="lazy" alt="Traction circle for Driver Two">
    <img src="/images/traction_driver_comparison.png" loading="lazy" alt="Traction circle driver comparison">
  </div>
  <em>Traction circle for Driver One (left), traction circle for Driver Two (middle), and traction circle comparison between drivers (right).</em>
</div>

By combining the data from all five drivers, the resulting traction circle demonstrates the overall performance the vehicle is capable of relative to the five drivers who participated in the driving event. The overall traction circle shows a maximum lateral acceleration of approximately 1.5 g's, which agrees with the predicted maximum lateral acceleration used to design the 2018 vehicle's suspension.

<div class="gallery-box">
  <div class="gallery_two">
    <img src="/images/traction_overall.png" loading="lazy" alt="Traction circle overall results">
  </div>
  <em>Traction circle results among all five drivers.</em>
</div>

Data from the linear potentiometers was analyzed for the skidpad course. We determined the weight on the front and rear tires and the lateral force produced by the right tires using elementary force balances throughout the event.

<div class="gallery-box">
  <div class="gallery_three">
    <img src="/images/traction_front_force.png" loading="lazy" alt="Weight on front tires">
    <img src="/images/traction_rear_force.png" loading="lazy" alt="Weight on rear tires">
    <img src="/images/traction_lateral_force.png" loading="lazy" alt="Lateral force on right tires">
  </div>
  <em>With linear potentiometer results, we approximated the weight on the front tires (left), the weight on the rear tires (middle), and the lateral force experienced by the right tires (right) along the skidpad course.</em>
</div>

A 40-page paper published by the American Society for Engineering Education further detailing the course that allowed us the opportunity to obtain this data, sensor selection justification, and a full description of how the traction circle was generated can be found <a href="https://peer.asee.org/measuring-the-traction-limits-and-suspension-forces-of-a-formula-sae-racecar" target="_blank">here</a>.
