# Task 11: Root Finding – Newton-Raphson and Secant Methods

## Mathematical concept

Newton-Raphson uses a derivative to update an estimate, while the secant method estimates the slope using two previous points and does not require an explicit derivative.

## Input values / parameters

- Cash flows = [-10000, 3000, 3500, 4000, 2500].
- Newton initial guess = 0.10.
- Secant initial guesses = 0.05 and 0.20.
- Tolerance = 10⁻¹².

## Mathematical operation

The NPV function is set equal to zero. Newton-Raphson uses NPV and its derivative, while the secant method uses two initial rate estimates.

## Parameter change and effect

If the initial guesses are changed, the number of iterations and convergence behaviour can change. A poor initial guess can make Newton's method less reliable for some nonlinear functions.

## Output and interpretation

The root is the interest rate at which the net present value is approximately zero. Agreement between Newton-Raphson and secant results gives confidence in the computed rate.

## Python implementation

Source code: [`task_11.py`](task_11.py)

```python
from scipy.optimize import root_scalar

cash_flows = [-10000, 3000, 3500, 4000, 2500]

def npv(rate):
    return sum(cf / (1 + rate)**t
               for t, cf in enumerate(cash_flows))

def d_npv(rate):
    return sum(-t * cf / (1 + rate)**(t + 1)
               for t, cf in enumerate(cash_flows)
               if t > 0)

newton = root_scalar(
    npv, fprime=d_npv, x0=0.10,
    method="newton", xtol=1e-12
)

secant = root_scalar(
    npv, x0=0.05, x1=0.20,
    method="secant", xtol=1e-12
)

print(f"IRR using Newton-Raphson: {newton.root:.6%}")
print(f"IRR using Secant method: {secant.root:.6%}")
print(f"NPV at Newton solution: {npv(newton.root):.6f}")
```

Run it with:

```bash
python task_11.py
```
