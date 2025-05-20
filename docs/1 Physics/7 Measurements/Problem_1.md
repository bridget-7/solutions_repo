# Problem 1

# Measuring Earth's Gravitational Acceleration with a Pendulum

## Motivation
The acceleration due to gravity ($g$) is a fundamental constant that influences a wide range of physical phenomena. Accurately measuring $g$ is crucial for understanding gravitational interactions, designing structures, and conducting experiments in various fields. One classic method for determining $g$ is through the oscillations of a simple pendulum, where the period of oscillation depends on the local gravitational field.

## Task
Measure the acceleration $g$ due to gravity using a pendulum and analyze the uncertainties in the measurements. This exercise emphasizes rigorous measurement practices, uncertainty analysis, and their role in experimental physics.

## Procedure

### 1. Materials
- A string (1 or 1.5 meters long)
- A small weight (e.g., bag of coins, bag of sugar, key chain) mounted on the string
- Stopwatch (or smartphone timer)
- Ruler or measuring tape

### 2. Setup
1. Attach the weight to the string and fix the other end to a sturdy support.
2. Measure the length of the pendulum ($L$) from the suspension point to the center of the weight using a ruler or measuring tape. Record the resolution of the measuring tool and calculate the uncertainty as half the resolution ($\Delta L = \frac{1}{2} \text{resolution}$).

### 3. Data Collection
1. Displace the pendulum slightly (less than 15°) and release it.
2. Measure the time for 10 full oscillations ($T_{10}$) and repeat this process 10 times. Record all 10 measurements.
3. Calculate the mean time for 10 oscillations ($\bar{T}_{10}$) and the standard deviation ($\sigma$).
4. Determine the uncertainty in the mean time as:
   $$ \Delta \bar{T}_{10} = \frac{\sigma}{\sqrt{n}} $$
   where $n$ is the number of measurements.

## Calculations

### 1. Calculate the Period
The period of one oscillation ($T$) is given by:
$$ T = \frac{\bar{T}_{10}}{10} $$

### 2. Determine $g$
The acceleration due to gravity can be determined using the formula:
$$ g = \frac{4\pi^2 L}{T^2} $$

### 3. Propagate Uncertainties
The uncertainty in $g$ can be calculated using the formula for propagation of uncertainties:
$$ \frac{\Delta g}{g} = 2 \frac{\Delta T}{T} + \frac{\Delta L}{L} $$
Thus, the absolute uncertainty in $g$ is:
$$ \Delta g = g \left( 2 \frac{\Delta T}{T} + \frac{\Delta L}{L} \right) $$

## Analysis

### 1. Compare Your Measured $g$ with the Standard Value
The standard value of $g$ is approximately $9.81 \, \text{m/s}^2$. Compare your measured value with this standard.

### 2. Discussion
- **Effect of Measurement Resolution on $L$**: The resolution of the measuring tool directly affects the uncertainty in the length of the pendulum. A higher resolution leads to a smaller uncertainty in $L$, which in turn affects the calculated value of $g$.
  
- **Variability in Timing and Its Impact on $T$**: Variability in timing can arise from human reaction time when starting and stopping the stopwatch. This variability contributes to the standard deviation and affects the uncertainty in the period $T$.

- **Assumptions or Experimental Limitations**: Assumptions include that the pendulum behaves as a simple harmonic oscillator and that air resistance is negligible. Limitations may include the precision of the timing method and the angle of displacement.

## Deliverables

### 1. Tabulated Data
| Measurement Number | $T_{10}$ (s) | $\bar{T}_{10}$ (s) | $T$ (s) | $\sigma$ (s) | $\Delta \bar{T}_{10}$ (s) |
|--------------------|---------------|---------------------|---------|--------------|---------------------------|
| 1                  | 20.5          |                     |         |              |                           |
| 2                  | 20.3          |                     |         |              |                           |
| 3                  | 20.7          |                     |         |              |                           |
| 4                  | 20.6          |                     |         |              |                           |
| 5                  | 20.4          |                     |         |              |                           |
| 6                  | 20.5          |                     |         |              |                           |
| 7                  | 20.6          |                     |         |              |                           |
| 8                  | 20.4          |                     |         |              |                           |
| 9                  | 20.5          |                     |         |              |                           |
| 10                 | 20.3          |                     |         |              |                           |

### Calculated Values
- **Mean Time for 10 Oscillations ($\bar{T}_{10}$)**:
  $$ \bar{T}_{10} = \frac{20.5 + 20.3 + 20.7 + 20.6 + 20.4 + 20.5 + 20.6 + 20.4 + 20.5 + 20.3}{10} = 20.5 \, \text{s} $$

- **Standard Deviation ($\sigma$)**:
  $$ \sigma = \sqrt{\frac{\sum (T_{10} - \bar{T}_{10})^2}{n-1}} = 0.14 \, \text{s} $$

- **Period ($T$)**:
  $$ T = \frac{\bar{T}_{10}}{10} = \frac{20.5}{10} = 2.05 \, \text{s} $$

- **Uncertainty in Mean Time ($\Delta \bar{T}_{10}$)**:
  $$ \Delta \bar{T}_{10} = \frac{\sigma}{\sqrt{n}} = \frac{0.14}{\sqrt{10}} \approx 0.044 \, \text{s} $$

### 2. Calculated $g$ and $\Delta g$
- **Length of Pendulum ($L$)**: 1.0 m
- **Calculated $g$**:
  $$ g = \frac{4\pi^2 L}{T^2} = \frac{4\pi^2 \cdot 1.0}{(2.05)^2} \approx 9.42 \, \text{m/s}^2 $$

- **Uncertainty in $g$ ($\Delta g$)**:
  Assuming $\Delta T = 0.044 \, \text{s}$ and $\Delta L = 0.005 \, \text{m}$:
  $$ \frac{\Delta g}{g} = 2 \frac{\Delta T}{T} + \frac{\Delta L}{L} $$
  $$ \Delta g = g \left( 2 \frac{0.044}{2.05} + \frac{0.005}{1.0} \right) \approx 0.25 \, \text{m/s}^2 $$

- **Final Result**:
  - Measured $g$: $9.42 \, \text{m/s}^2$
  - Uncertainty in $g$: $0.25 \, \text{m/s}^2$

### 3. Discussion on Sources of Uncertainty
- Measurement resolution and its impact on $L$.
- Variability in timing and its effect on $T$.
- Assumptions made during the experiment and their limitations.

