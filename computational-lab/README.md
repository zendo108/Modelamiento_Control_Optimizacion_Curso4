# Taller Computacional: Bioreactor ODE Simulation and Multi-Objective Optimization

This project implements a simulation and optimization framework for modeling the operation of a fed-batch bioreactor. It involves solving Ordinary Differential Equations (ODEs) using numerical methods, performing single-objective and multi-objective optimization, and visualizing results.

## Project Structure
The project is divided into the following sections:

1. **ODE System Definition:**
   - Defines the differential equations governing the bioreactor's state variables: biomass, substrate, product, and volume.
   - Implements constitutive equations for growth rate, substrate consumption, and product formation.

2. **Numerical Solvers:**
   - **Euler's Method:** Explicit method for solving ODEs.
   - **Runge-Kutta 4th Order (RK4):** Higher-order solver for more accurate integration.

3. **Integration and Visualization:**
   - Simulates the ODE system using the defined numerical solvers.
   - Compares results against SciPy's `solve_ivp` for stiff ODEs using methods like `BDF` or `Radau`.

4. **Optimization:**
   - Implements a single-objective optimization using `scipy.optimize` for maximizing product output.
   - Performs multi-objective optimization using the `NSGA-II` algorithm from the `pymoo` library to balance conflicting objectives.

5. **Visualization:**
   - Plots results from the integration and optimization processes, including control strategies and Pareto fronts.

---

## Setup Instructions

### Prerequisites
Ensure you have the following installed:
- Python 3.8 or higher
- Conda or virtualenv (recommended for managing environments)

### Environment Setup
Create and activate a virtual environment:
```bash
# Create virtual environment
conda create --name bioreactor_env python=3.9 -y

# Activate the environment
conda activate bioreactor_env
```

Install the required dependencies:
```bash
pip install numpy scipy matplotlib pymoo
```

If you encounter a warning about non-compiled modules in `pymoo`, it can be safely ignored or suppressed:
```python
from pymoo.config import Config
Config.warnings['not_compiled'] = False
```

---

## Usage Instructions

### Running the Project
Run the Jupyter notebook file `Taller_Solution.ipynb` to execute the code. It includes all steps, from defining the ODE system to performing multi-objective optimization.

### Key Sections in the Code:
1. **ODE System:**
   ```python
   def fed_batch(t, x, u, Csf):
       # Define differential equations and constitutive equations
       ...
       return np.array([dXdt, dSdt, dPdt, dVdt])
   ```

2. **Numerical Solvers:**
   - Euler's Method:
     ```python
     def Euler_method(f, t0, tf, x0, n, u, p):
         # Implements explicit Euler integration
         ...
     ```
   - RK4 Method:
     ```python
     def RK4_method(f, t0, tf, x0, n, u, p):
         # Implements 4th order Runge-Kutta method
         ...
     ```

3. **Integration and Comparison:**
   Compare `Euler` and `RK4` with SciPy solvers:
   ```python
   t1, x1 = Euler_method(...)
   t2, x2 = RK4_method(...)
   sol = solve_ivp(fed_batch, ...)
   ```

4. **Optimization:**
   - Single-objective using `scipy.optimize`:
     ```python
     from scipy.optimize import minimize
     solution = minimize(...)
     ```
   - Multi-objective using NSGA-II:
     ```python
     from pymoo.algorithms.moo.nsga2 import NSGA2
     from pymoo.optimize import minimize
     res = minimize(problem, algorithm, ...)
     ```

5. **Visualization:**
   Generate control strategies and Pareto front:
   ```python
   plt.plot(t, u_opt)
   plt.plot(res.F[:, 0], res.F[:, 1], 'o')
   ```

---

## Output
- **Time evolution of state variables:** Biomass, substrate, product, and volume as a function of time.
- **Control strategies:** Optimal feed rate profiles for the bioreactor.
- **Pareto front:** Trade-offs between competing objectives, such as maximizing product rate versus efficiency.

---

## Acknowledgments
This project is based on a computational lab for simulating and optimizing fed-batch bioreactors using Python and related scientific libraries.

---

## References
- [SciPy Documentation](https://docs.scipy.org/)
- [Matplotlib Documentation](https://matplotlib.org/)
- [pymoo Documentation](https://pymoo.org/)
