# Task 5: Matrix Algebra and Matrix Operations

## Mathematical concept

A matrix stores values in rows and columns. Matrix multiplication combines rows of one matrix with columns of another. A determinant can also be used to check properties of a square matrix.

## Input values / parameters

- Four points representing the corners of a square.
- Rotation angle = 45 degrees.
- Scale factors = 2.0 in x and 1.5 in y.

## Mathematical operation

The program creates a rotation matrix and a scaling matrix, combines them using matrix multiplication, and applies the resulting transformation to the points.

## Parameter change and effect

If the rotation angle is changed from 45° to 90°, the square points rotate further around the origin. If a scale factor is increased, the corresponding dimension of the transformed object becomes larger.

## Output and interpretation

The transformed points are the new coordinates after scaling and rotation. The determinant of the transformation indicates the area-scaling factor and also confirms that the transformation is non-singular when the determinant is non-zero.

## Python implementation

Source code: [`task_05.py`](task_05.py)

```python
import numpy as np

points = np.array([
    [0.0, 0.0],
    [1.0, 0.0],
    [1.0, 1.0],
    [0.0, 1.0]
])

angle = np.deg2rad(45)

rotation = np.array([
    [np.cos(angle), -np.sin(angle)],
    [np.sin(angle), np.cos(angle)]
])

scale = np.array([
    [2.0, 0.0],
    [0.0, 1.5]
])

transformation = rotation @ scale
transformed_points = points @ transformation.T

print("Original points:\n", points)
print("Transformation matrix:\n", transformation)
print("Transformed points:\n", transformed_points)
print("Determinant:", np.linalg.det(transformation))
```

Run it with:

```bash
python task_05.py
```
