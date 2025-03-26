import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

def projectile_motion(t, y, g):
    """
    Differential equations for projectile motion.
    y = [x, vx, y, vy]
    """
    dxdt = y[1]  # Velocity in x-direction
    dvxdt = 0    # No acceleration in x (ignoring air resistance)
    dydt = y[3]  # Velocity in y-direction
    dvydt = -g   # Acceleration due to gravity
    return [dxdt, dvxdt, dydt, dvydt]

def simulate_projectile(v0, theta, g=9.81):
    """Simulates projectile motion given initial velocity and angle."""
    theta_rad = np.radians(theta)
    y0 = [0, v0 * np.cos(theta_rad), 0, v0 * np.sin(theta_rad)]  # Initial conditions
    
    t_span = (0, 2 * v0 * np.sin(theta_rad) / g)  # Estimated flight time
    sol = solve_ivp(projectile_motion, t_span, y0, args=(g,), dense_output=True)
    
    t_vals = np.linspace(0, sol.t_events[0] if sol.t_events else t_span[1], 100)
    traj = sol.sol(t_vals)
    return traj[0], traj[2]  # Return x and y values

def plot_range_vs_angle(v0_values, g_values):
    """Plots range vs angle for different velocities and gravity values."""
    angles = np.linspace(0, 90, 100)
    plt.figure(figsize=(8, 6))
    
    for v0 in v0_values:
        for g in g_values:
            ranges = [(v0**2 * np.sin(2 * np.radians(theta)) / g) for theta in angles]
            plt.plot(angles, ranges, label=f'v0={v0} m/s, g={g} m/s²')
    
    plt.xlabel("Launch Angle (degrees)")
    plt.ylabel("Range (meters)")
    plt.title("Projectile Range vs Launch Angle")
    plt.legend()
    plt.grid()
    plt.show()

# Example usage
v0_values = [10, 20, 30]  # Different initial velocities
g_values = [9.81]         # Standard gravity
plot_range_vs_angle(v0_values, g_values)
