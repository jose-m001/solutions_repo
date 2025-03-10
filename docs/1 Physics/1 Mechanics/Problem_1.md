# Problem 1

1. Theoretical Foundation

Governing Equations of Motion

 - A projectile's motion can be split into two components:

 
   - Horizontal motion (x-direction):
 
              𝑥(𝑡)=𝑣0cos⁡(𝜃)⋅𝑡

   - Vertical motion (y-direction):

              𝑦(𝑡)=𝑣0sin⁡(𝜃)⋅𝑡−12𝑔𝑡2

 - The time of flight (𝑇) is derived by setting 𝑦(𝑡)=0y(t)=0 (when the projectile hits the ground):

              𝑇=2𝑣0sin⁡(𝜃)𝑔

 - The horizontal range (𝑅R) is given by:

              𝑅=𝑣0cos(𝜃)⋅𝑇

    Substituting 𝑇:

              𝑅=𝑣02sin(2𝜃)𝑔
 
Effect of Initial Conditions

 - Initial Velocity (𝑣0): Affects the maximum range; higher 𝑣0 increases 𝑅.

 - Gravitational Acceleration (g): Affects how fast the projectile falls, reducing 𝑅 as 𝑔 increases.

 - Launch Angle (𝜃): The range depends on sin(2𝜃)sin(2θ), peaking at 𝜃=45∘.

2. Analysis of the Range

 - The range 𝑅 as a function of 𝜃 follows:

              𝑅(𝜃)=𝑣02𝑔sin(2𝜃)

    - It is a parabolic function of sin(2𝜃), with a maximum at 𝜃=45∘.

Influence of Parameters

  1. Initial Velocity (𝑣0):

    - Doubling 𝑣0 quadruples the range (𝑅∝𝑣02).

  2. Gravitational Acceleration (𝑔):

    - Higher 𝑔 reduces the range (𝑅∝1/𝑔).

  3. Angle of Projection (𝜃):

    - The range peaks at 45∘ and is symmetric about it.

3. Practical Applications

 - Uneven Terrain: Adjust 𝑦(𝑡) to account for non-zero launch or landing height:

              𝑦(𝑡)=𝑦0+𝑣0sin(𝜃)⋅𝑡−12𝑔𝑡2

   Solve for 𝑇 using the quadratic formula, and substitute 𝑇 into 𝑥(𝑡)x(t) for the adjusted range.

 - Air Resistance: Introduce a drag force proportional to velocity:
              𝐹drag=−𝑘𝑣

   This leads to coupled differential equations, requiring numerical methods for solutions.

4. Implementation

Steps for Simulation

1. Algorithm:

   - Input parameters: 𝑣0, 𝑔,𝜃,𝑦0.

   - Calculate range 𝑅 for various 𝜃 values (e.g., from 0∘ to 90∘).

2. Visualization:
   
   - Plot 𝑅 vs. 𝜃 for different 𝑣0, 𝑔, or 𝑦0.

   - Overlay plots to compare how each parameter influences the range.

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