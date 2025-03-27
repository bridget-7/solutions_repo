import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Define the forced damped pendulum equations
def pendulum(t, y, q, F, omega):
    theta, omega_dot = y
    dtheta_dt = omega_dot
    domega_dt = -q * omega_dot - np.sin(theta) + F * np.cos(omega * t)
    return [dtheta_dt, domega_dt]

# Parameters
t_max = 100  # Max time
q = 0.5  # Damping coefficient
F = 1.2  # Driving force amplitude
omega = 2/3  # Driving frequency

# Initial conditions
y0 = [0.2, 0]  # Initial angle and angular velocity

# Time points for evaluation
t_eval = np.linspace(0, t_max, 5000)

# Solve the ODE using Runge-Kutta method
sol = solve_ivp(pendulum, [0, t_max], y0, args=(q, F, omega), t_eval=t_eval, method='RK45')

theta = sol.y[0]
omega_dot = sol.y[1]

# Phase portrait plot
plt.figure(figsize=(8, 6))
plt.plot(theta, omega_dot, '.', markersize=0.5, label='Phase Space')
plt.xlabel("Theta (rad)")
plt.ylabel("Angular velocity (rad/s)")
plt.title("Phase Portrait of the Forced Damped Pendulum")
plt.legend()
plt.grid()
plt.show()

# Poincaré section (sampling at integer multiples of driving period)
T = (2 * np.pi) / omega  # Driving period
poincare_theta = []
poincare_omega = []

for i in range(len(t_eval)):
    if np.isclose(t_eval[i] % T, 0, atol=0.05):
        poincare_theta.append(theta[i])
        poincare_omega.append(omega_dot[i])

# Poincaré section plot
plt.figure(figsize=(8, 6))
plt.plot(poincare_theta, poincare_omega, 'ro', markersize=2, label='Poincaré Points')
plt.xlabel("Theta (rad)")
plt.ylabel("Angular velocity (rad/s)")
plt.title("Poincaré Section of the Forced Damped Pendulum")
plt.legend()
plt.grid()
plt.show()
