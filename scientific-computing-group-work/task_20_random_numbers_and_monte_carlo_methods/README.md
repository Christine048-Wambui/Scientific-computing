# Task 20: Random Numbers and Monte Carlo Methods

## Mathematical concept

Monte Carlo methods estimate probabilities or other quantities by repeated random sampling. As the number of simulations increases, the observed proportion tends to approach the underlying probability.

## Input values / parameters

- Server capacity = 1000 units.
- Mean demand = 850 units.
- Demand standard deviation = 120 units.
- Number of simulations N = 100,000.
- Random-number seed = 42.

## Mathematical operation

Generate normally distributed demand values, count the cases where demand exceeds capacity, and divide the number of overload cases by the total simulations.

## Parameter change and effect

If N is increased, the estimate should generally become more stable because more random samples are used. If the standard deviation is increased, more high-demand scenarios are expected and the overload probability can rise.

## Output and interpretation

The estimated probability is the proportion of simulated scenarios in which demand is above server capacity. The convergence graph shows how the running estimate stabilizes as more simulations are performed.

## Graph interpretation

The running probability usually fluctuates strongly at the beginning and becomes more stable as the number of simulations increases. This illustrates Monte Carlo convergence.

## Python implementation

Source code: [`task_20.py`](task_20.py)

```python
import numpy as np
import matplotlib.pyplot as plt

rng = np.random.default_rng(42)

capacity = 1000.0
mean_demand = 850.0
std_demand = 120.0
N = 100_000

demand = rng.normal(mean_demand, std_demand, N)
overloaded = demand > capacity
overload_probability = overloaded.mean()

print(f"Estimated overload probability: {overload_probability:.4%}")
print(f"Number of overload cases: {overloaded.sum()} out of {N}")

running_probability = (
    np.cumsum(overloaded) / np.arange(1, N + 1)
)

indices = np.unique(
    np.logspace(1, np.log10(N), 200).astype(int)
) - 1

plt.semilogx(
    indices + 1,
    running_probability[indices]
)
plt.xlabel("Number of simulations")
plt.ylabel("Estimated overload probability")
plt.title("Monte Carlo estimate of server-overload risk")
plt.grid(True)
plt.show()
```

Run it with:

```bash
python task_20.py
```
