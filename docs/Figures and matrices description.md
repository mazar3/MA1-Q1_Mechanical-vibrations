# Description of Satellite Data and Models

This document describes three technical figures regarding the physical modeling, parameters, and attitude control of a satellite equipped with flexible appendages (solar arrays and deployable antenna).

## 1. Table 1: Satellite Parameters (`Table.png`)

This image is a data table listing the physical properties of the various satellite components.

**Table Title:** Table 1: Parameters of the satellite

| Parameter | Value | Unit |
| --- | --- | --- |
| **Solar array length** | 8 |  |
| **Solar array mass density** (Linear mass density) | 2.86 |  |
| **Solar flexural rigidity** | 4072 |  |
| **Deployable arm length** | 8 |  |
| **Deployable arm mass density** (Linear mass density) | 2.29 |  |
| **Deployable arm flexural rigidity** |  |  |
| **Deployable antenna diameter** | 20 |  |
| **Main body mass** | 640 |  |
| **Main body inertia** | 426.7 |  |
| **Deployable antenna areal density** | 0.3 |  |
| **Deployable antenna diameter** (Repeated line) | 20 |  |

---

## 2. Figure 1: Satellite Model (`model.png`)

This image shows two distinct diagrams, annotated as being taken from "[Wei et al, 2023]".

**Global Legend:** Figure 1: Satellite drawing (left), degrees of freedom retained in the dynamic model.

### Left Image: 3D Satellite Drawing

A visual rendering (wireframe/CAD type) showing the global architecture:

* **Main-body:** A cubic central body.
* **Solar array:** Two rectangular solar array wings extending on either side of the main body.
* **Deployable arm:** A long pole (beam) descending from the main body.
* **Deployable antenna:** A large parabolic antenna (represented by a mesh) attached to the end of the deployable arm.

### Right Image: Kinematic Diagram (Degrees of Freedom)

A simplified schematic representation used for dynamic modeling, showing coordinates and degrees of freedom:

* **Central Body:** Represented by a gray square in the center. It has a local frame $O_b-x_by_b$ and a rotation angle $\theta$.
* **Solar Arrays (Horizontal Arms):** Represented by two horizontal lines extending from the center. Vertical arrows indicate the degrees of freedom for flexible deformation (vibration):
    * Left side: $w_1, w_2$
    * Right side: $w_3, w_4$
* **Antenna Arm (Vertical Link):** A vertical line descending from the central square downwards.
* **Antenna (Base):** Represented by a flat gray rectangle at the bottom of the vertical line. It has a local frame $O_a-x_ay_a$ and an angle $\alpha$.

---

## 3. Figure 2: Control Torque Profile (`Torque.png`)

This image is a time graph showing the command applied to the satellite.

**Graph Title:** Figure 2: Torque ($u$) applied to the satellite for position control

**Axes:**

* **X-Axis (Abscissa):** Time in seconds (`time (sec)`), graduated from 0 to 40.
* **Y-Axis (Ordinate):** Torque in Newton-meters (`Torque (Nm)`), graduated from -40 to 40.

**Curve Description:**
The curve represents a smoothed "Bang-Bang" type maneuver (sinusoidal shape over one period) followed by a rest phase:

1.  **0 to 10 seconds:** The torque increases positively to reach a peak of **+40 Nm** (around t=5s), then descends to cross zero at t=10s.
2.  **10 to 20 seconds:** The torque becomes negative, reaching a trough of **-40 Nm** (around t=15s), then rises to reach zero at t=20s.
3.  **20 to 40 seconds:** The torque remains constant at **0 Nm**.

This indicates a control impulse active during the first 20 seconds, likely intended to perform a rotation of the satellite, followed by a coasting (or holding) phase with no torque applied.

# K_matrix.csv
22922,0,91688,0,0,0,0,-22922,0,91687
0,1.4679e+06,-8.2306e-11,-599.89,163.61,-599.89,163.61,0,-1.467e+06,0
91687,2.0212e-10,4.9598e+05,1308.9,-218.14,-1308.9,218.14,-91687,0,2.445e+05
0,-599.89,1308.9,872.57,-272.68,0,0,0,0,0
0,163.61,-218.14,-272.68,109.07,0,0,0,0,0
0,-599.89,-1308.9,0,0,872.57,-272.68,0,0,0
0,163.61,218.14,0,0,-272.68,109.07,0,0,0
-22922,0,-91687,0,0,0,0,22922,0,-91687
0,-1.467e+06,0,0,0,0,0,0,1.467e+06,0
91687,0,2.445e+05,0,0,0,0,-91688,0,4.89e+05

# C_matrix.csv
692.56,0,7.677,0,0,0,0,2.3554,0,-4.5364
0,656.3,4.563e-14,0.87217,-0.65705,0.87217,-0.65705,0,3.0533,0
7.677,4.5963e-14,443.7,-0.6804,0.81381,0.6804,-0.81381,4.5364,0,-8.3749
0,0.87217,-0.6804,10.193,2.0095,0,0,0,0,0
0,-0.65705,0.81381,2.0095,3.1418,0,0,0,0,0
0,0.87217,0.6804,0,0,10.193,2.0095,0,0,0
0,-0.65705,-0.81381,0,0,2.0095,3.1418,0,0,0
2.3554,0,4.5364,0,0,0,0,101.05,0,-7.677
0,3.0533,0,0,0,0,0,0,100.35,0
-4.5364,0,-8.3749,0,0,0,0,-7.677,0,2398.8