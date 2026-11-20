# Task 2: NumPy Arrays and Numerical Computation

## Mathematical concept

An array stores an organized collection of numerical values. NumPy can calculate statistics and perform an operation on every array element without writing a separate loop.

## Input values / parameters

- 24 hourly temperature readings in degrees Celsius.
- The conversion formula F = 1.8C + 32.
- The required statistics are mean, minimum and maximum.

## Mathematical operation

Calculate mean, minimum and maximum of the Celsius array, then apply the Celsius-to-Fahrenheit formula element by element.

## Parameter change and effect

If the temperature at one hour is changed from 18.5°C to 20.5°C, the daily mean increases because the total of the readings increases. The converted Fahrenheit value for that reading also increases.

## Output and interpretation

The output gives a summary of the day's temperatures. The mean represents the average daily temperature, while the minimum and maximum show the lowest and highest readings. The Fahrenheit array gives the same measurements in another unit.

## Python implementation

Source code: [`task_02.py`](task_02.py)

```python
import numpy as np

temperatures_c = np.array([
    18.5, 18.0, 17.8, 17.5, 17.9, 19.0,
    21.5, 23.8, 25.6, 27.1, 28.3, 29.0,
    29.4, 29.1, 28.5, 27.6, 26.2, 24.8,
    23.4, 22.1, 21.0, 20.2, 19.6, 19.0
])

mean_temp = np.mean(temperatures_c)
min_temp = np.min(temperatures_c)
max_temp = np.max(temperatures_c)
temperatures_f = 1.8 * temperatures_c + 32

print(f"Daily mean temperature: {mean_temp:.2f} C")
print(f"Minimum temperature: {min_temp:.2f} C")
print(f"Maximum temperature: {max_temp:.2f} C")
print("First six Fahrenheit readings:", temperatures_f[:6])
```

Run it with:

```bash
python task_02.py
```
