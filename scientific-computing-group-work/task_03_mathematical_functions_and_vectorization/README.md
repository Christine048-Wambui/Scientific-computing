# Task 3: Mathematical Functions and Vectorization

## Mathematical concept

Vectorization applies the same mathematical operation to many values at once. It is useful when a dataset contains a very large number of measurements.

## Input values / parameters

- One million simulated network-latency readings between 5 ms and 250 ms.
- Random-number seed = 42.
- Conversion from milliseconds to seconds and squaring of the converted value.

## Mathematical operation

For each value, seconds = latency_ms / 1000 and squared = seconds². The vectorized version performs these operations on the whole NumPy array.

## Parameter change and effect

If the upper latency limit is increased from 250 ms to 400 ms, the generated dataset can contain larger delays, so squared latency values can also become much larger. The exact timing also depends on the generated sample.

## Output and interpretation

The vectorized result contains squared latency values. The timing comparison demonstrates that NumPy vectorization can reduce the repeated Python-level loop overhead for large numerical arrays.

## Python implementation

Source code: [`task_03.py`](task_03.py)

```python
import numpy as np
import timeit

rng = np.random.default_rng(42)
latency_ms = rng.uniform(5, 250, 1_000_000)

def loop_version():
    squared = []
    for value in latency_ms:
        seconds = value / 1000.0
        squared.append(seconds ** 2)
    return squared

def vectorized_version():
    seconds = latency_ms / 1000.0
    return seconds ** 2

loop_time = timeit.timeit(loop_version, number=1)
vector_time = timeit.timeit(vectorized_version, number=3) / 3
result = vectorized_version()

print("First five squared latency values:", result[:5])
print(f"Loop time: {loop_time:.4f} s")
print(f"Vectorized time: {vector_time:.4f} s")
print(f"Approximate speed-up: {loop_time/vector_time:.1f}x")
```

Run it with:

```bash
python task_03.py
```
