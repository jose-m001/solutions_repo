# Problem 3

# Trajectories of a Freely Released Payload Near Earth

## Motivation

When an object is released from a moving rocket near Earth, its trajectory is determined by the interplay of initial conditions and gravitational forces. 

This scenario blends principles of orbital mechanics with computational techniques to solve complex motion equations. 

Understanding these trajectories is essential for space mission operations, such as deploying payloads into orbit or ensuring safe reentry to Earth.

---

## Deliverables
1 . **Markdown Document:** Detailed explanation of trajectory analysis.

2 . **Python Script:** Numerical simulation of payload motion.

3 . **Graphical Representations:**
    
-  Orbital trajectories for different initial velocities and positions.
    
    
-  Comparison of parabolic, hyperbolic, and elliptical trajectories.


## Theoretical Foundation

### Governing Equations

The motion of a payload near Earth can be described using Newton's Law of Gravitation:

$$
F = \frac{G M m}{r^2},
$$

where:
- $(G)$ is the gravitational constant,
- \( M \) is Earth's mass,
- \( m \) is the payload's mass,
- \( r \) is the distance between the payload and Earth's center.

The acceleration due to gravity is given by:

$$
a = \frac{F}{m} = \frac{G M}{r^2}.
$$

Using Newton's Second Law, the equations of motion for the payload in Cartesian coordinates \((x, y)\) are:

$$
\ddot{x} = -\frac{G M x}{r^3}, \quad \ddot{y} = -\frac{G M y}{r^3},
$$

where \( r = \sqrt{x^2 + y^2} \).

### Trajectory Classification
The type of trajectory depends on the total energy \( E \) of the system:
- **Elliptical:** \( E < 0 \)
- **Parabolic:** \( E = 0 \)
- **Hyperbolic:** \( E > 0 \)

The energy is given by:

\[
E = \frac{1}{2}mv^2 - \frac{G M m}{r}.
\]

---

## Computational Implementation

### Numerical Simulation
Using numerical methods, such as the Runge-Kutta algorithm, we can compute the payload’s trajectory based on its initial position and velocity.

#### Python Script
```python
import numpy as np
import matplotlib.pyplot as plt

# Gravitational constant (m^3 kg^-1 s^-2)
G = 6.67430e-11

# Mass of Earth (kg)
M = 5.972e24

# Earth's radius (m)
R_earth = 6.371e6

# Time step and duration
dt = 1  # seconds
simulation_time = 3600  # seconds

# Initial conditions (position in meters, velocity in m/s)
initial_position = np.array([R_earth + 500e3, 0])  # 500 km altitude
initial_velocity = np.array([0, 7500])  # near-orbital velocity

# Initialize arrays for position and velocity
position = [initial_position]
velocity = [initial_velocity]

# Function to compute acceleration
def acceleration(pos):
    r = np.linalg.norm(pos)
    return -G * M * pos / r**3

# Numerical integration loop
for _ in range(int(simulation_time / dt)):
    current_pos = position[-1]
    current_vel = velocity[-1]

    # Compute acceleration
    acc = acceleration(current_pos)

    # Update velocity and position using Euler's method
    new_vel = current_vel + acc * dt
    new_pos = current_pos + new_vel * dt

    velocity.append(new_vel)
    position.append(new_pos)

# Convert to numpy arrays
position = np.array(position)

# Plot trajectory
plt.figure(figsize=(8, 8))
plt.plot(position[:, 0], position[:, 1], label="Payload Trajectory")
plt.scatter(0, 0, color="blue", label="Earth", s=500)
plt.xlabel("x (m)")
plt.ylabel("y (m)")
plt.title("Payload Trajectory Near Earth")
plt.legend()
plt.grid()
plt.axis('equal')
plt.show()
```

---

## Discussion

### Applications
- **Orbital Insertion:** Achieving stable orbits for satellites.
- **Reentry Analysis:** Predicting paths for safe reentry of payloads.
- **Escape Scenarios:** Determining conditions for interplanetary missions.

### Limitations
- **Simplifications:** Assumes a point-mass Earth and neglects atmospheric drag.
- **Perturbations:** Ignores gravitational effects from other celestial bodies.

By analyzing the dynamics of a payload released near Earth, we can gain deeper insights into orbital mechanics and enhance the design of space missions.

