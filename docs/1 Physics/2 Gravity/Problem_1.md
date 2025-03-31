import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp
import matplotlib.animation as animation

# Constants
G = 6.67430e-11  # Gravitational constant (m^3 kg^-1 s^-2)
M = 5.972e24      # Mass of the Earth (kg)

# Function to compute derivatives
def orbit_eq(t, y):
    x, vx, y, vy = y
    r = np.sqrt(x**2 + y**2)
    if r == 0:
        return [vx, 0, vy, 0]  # Prevent division by zero
    ax = -G * M * x / r**3
    ay = -G * M * y / r**3
    return [vx, ax, vy, ay]

# Function to compute orbital period and trajectory
def compute_orbit(r0):
    v0 = np.sqrt(G * M / r0)  # Circular orbit velocity
    y0 = [r0, 0, 0, v0]
    t_span = [0, 2 * np.pi * r0 / v0 * 2]  # Ensure full orbit is captured
    sol = solve_ivp(orbit_eq, t_span, y0, t_eval=np.linspace(0, t_span[1], 1000))
    
    # Find period using zero crossing of x-axis (returning to initial position)
    x_positions = sol.y[0]
    zero_crossings = np.where(np.diff(np.sign(x_positions - r0)))[0]
    
    if len(zero_crossings) > 1:
        T = sol.t[zero_crossings[1]] - sol.t[zero_crossings[0]]
    else:
        T = t_span[1]
    
    return T, sol.y[0], sol.y[2]

# Simulating for different radii
radii = np.linspace(7e6, 4.2e7, 10)  # Various altitudes
periods = np.array([compute_orbit(r)[0] for r in radii])

# Plotting T^2 vs. r^3
plt.figure(figsize=(8,6))
plt.plot(radii**3, periods**2, 'o-', label='$T^2$ vs. $r^3$')
plt.xlabel('$r^3$ (m^3)')
plt.ylabel('$T^2$ (s^2)')
plt.title("Verification of Kepler's Third Law")
plt.legend()
plt.grid()
plt.show()

# Create an animation of the orbit
fig, ax = plt.subplots(figsize=(6,6))
ax.set_xlim(-radii[-1]*1.2, radii[-1]*1.2)
ax.set_ylim(-radii[-1]*1.2, radii[-1]*1.2)
ax.set_xlabel("X Position (m)")
ax.set_ylabel("Y Position (m)")
ax.set_title("Circular Orbit Simulation")

planet, = ax.plot([], [], 'bo', markersize=8, label="Orbiting Body")
trajectory, = ax.plot([], [], 'g-', linewidth=1, label="Orbit Path")
ax.legend()

# Get orbit data for animation
r0 = radii[5]  # Select a middle radius for visualization
T, x_vals, y_vals = compute_orbit(r0)

def init():
    planet.set_data([], [])
    trajectory.set_data([], [])
    return planet, trajectory

def update(frame):
    planet.set_data(x_vals[frame], y_vals[frame])
    trajectory.set_data(x_vals[:frame], y_vals[:frame])
    return planet, trajectory

ani = animation.FuncAnimation(fig, update, frames=len(x_vals), init_func=init, blit=True, interval=10)
plt.show()

# Ensure script runs properly in Visual Studio
if __name__ == "__main__":
    print("Simulation completed. Plot and animation displayed.")
