# Problem 1
1. Theoretical Foundation

Governing Equations of Motion

  - A projectile's motion can be split into two components:

Horizontal motion (x-direction):
𝑥(𝑡)= 𝑣0 cos(𝜃)⋅𝑡

Vertical motion (y-direction):
𝑦(𝑡)=𝑣0sin⁡(𝜃)⋅𝑡−1/2𝑔𝑡2

The time of flight (𝑇T) is derived by setting 𝑦(𝑡)=0y(t)=0 (when the projectile hits the ground):

𝑇=2𝑣0sin⁡(𝜃)𝑔

The horizontal range (𝑅R) is given by:

𝑅=𝑣0cos(𝜃)⋅𝑇
R=v 
0
​
 cos(θ)⋅T
Substituting 
𝑇
T:

𝑅
=
𝑣
0
2
sin
⁡
(
2
𝜃
)
𝑔
R= 
g
v 
0
2
​
 sin(2θ)
​
 
Effect of Initial Conditions
Initial Velocity (
𝑣
0
v 
0
​
 ): Affects the maximum range; higher 
𝑣
0
v 
0
​
  increases 
𝑅
R.
Gravitational Acceleration (
𝑔
g): Affects how fast the projectile falls, reducing 
𝑅
R as 
𝑔
g increases.
Launch Angle (
𝜃
θ): The range depends on 
sin
⁡
(
2
𝜃
)
sin(2θ), peaking at 
𝜃
=
45
∘
θ=45 
∘
 .
2. Analysis of the Range
The range 
𝑅
R as a function of 
𝜃
θ follows:
𝑅
(
𝜃
)
=
𝑣
0
2
𝑔
sin
⁡
(
2
𝜃
)
R(θ)= 
g
v 
0
2
​
 
​
 sin(2θ)
It is a parabolic function of 
sin
⁡
(
2
𝜃
)
sin(2θ), with a maximum at 
𝜃
=
45
∘
θ=45 
∘
 .
Influence of Parameters
Initial Velocity (
𝑣
0
v 
0
​
 ):
Doubling 
𝑣
0
v 
0
​
  quadruples the range (
𝑅
∝
𝑣
0
2
R∝v 
0
2
​
 ).
Gravitational Acceleration (
𝑔
g):
Higher 
𝑔
g reduces the range (
𝑅
∝
1
/
𝑔
R∝1/g).
Angle of Projection (
𝜃
θ):
The range peaks at 
45
∘
45 
∘
  and is symmetric about it.
3. Practical Applications
Uneven Terrain: Adjust 
𝑦
(
𝑡
)
y(t) to account for non-zero launch or landing height:
𝑦
(
𝑡
)
=
𝑦
0
+
𝑣
0
sin
⁡
(
𝜃
)
⋅
𝑡
−
1
2
𝑔
𝑡
2
y(t)=y 
0
​
 +v 
0
​
 sin(θ)⋅t− 
2
1
​
 gt 
2
 
Solve for 
𝑇
T using the quadratic formula, and substitute 
𝑇
T into 
𝑥
(
𝑡
)
x(t) for the adjusted range.
Air Resistance: Introduce a drag force proportional to velocity:
𝐹
drag
=
−
𝑘
𝑣
F 
drag
​
 =−kv
This leads to coupled differential equations, requiring numerical methods for solutions.
4. Implementation
Steps for Simulation
Algorithm:
Input parameters: 
𝑣
0
v 
0
​
 , 
𝑔
g, 
𝜃
θ, 
𝑦
0
y 
0
​
 .
Calculate range 
𝑅
R for various 
𝜃
θ values (e.g., from 
0
∘
0 
∘
  to 
90
∘
90 
∘
 ).
Visualization:
Plot 
𝑅
R vs. 
𝜃
θ for different 
𝑣
0
v 
0
​
 , 
𝑔
g, or 
𝑦
0
y 
0
​
 .
Overlay plots to compare how each parameter influences the range.
Python Code Example
python
Copy
Edit
import numpy as np
import matplotlib.pyplot as plt

# Constants
g = 9.8  # gravitational acceleration (m/s^2)

# Function to calculate range
def calculate_range(v0, theta, g):
    theta_rad = np.radians(theta)
    return (v0**2 * np.sin(2 * theta_rad)) / g

# Simulation parameters
v0 = 20  # initial velocity (m/s)
angles = np.linspace(0, 90, 500)  # angles from 0 to 90 degrees

# Calculate ranges
ranges = [calculate_range(v0, theta, g) for theta in angles]

# Plot
plt.figure(figsize=(8, 6))
plt.plot(angles, ranges, label=f'Initial Velocity = {v0} m/s')
plt.xlabel('Angle of Projection (degrees)')
plt.ylabel('Range (meters)')
plt.title('Projectile Range vs. Angle of Projection')
plt.legend()
plt.grid()
plt.show()
This approach provides a comprehensive analysis and practical insights, supported by a computational implementation for visualizing the relationship between the range and the angle of projection.
