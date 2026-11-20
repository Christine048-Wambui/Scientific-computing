# Task 9: Eigenvalues and Eigenvectors

## Mathematical concept

For a square matrix A, an eigenvector v satisfies Av = λv. The eigenvalue λ describes how the eigenvector is scaled by the transformation.

## Input values / parameters

- Adjacency matrix representing a four-node network.
- Nodes A, B, C and D.
- Dominant eigenvalue and corresponding eigenvector.

## Mathematical operation

Compute all eigenvalues and eigenvectors with np.linalg.eig(), select the dominant eigenvalue, and normalize its eigenvector to obtain relative node importance.

## Parameter change and effect

If one network connection is added or removed in the adjacency matrix, the eigenvalues and centrality scores can change because the network structure has changed.

## Output and interpretation

The centrality scores provide an eigenvector-based measure of structural importance. A higher score means that the node is relatively more connected to influential nodes in the network.

## Python implementation

Source code: [`task_09.py`](task_09.py)

```python
import numpy as np

A = np.array([
    [0., 1., 1., 0.],
    [1., 0., 1., 1.],
    [1., 1., 0., 1.],
    [0., 1., 1., 0.]
])

eigenvalues, eigenvectors = np.linalg.eig(A)
index = np.argmax(np.real(eigenvalues))
dominant_value = np.real(eigenvalues[index])
dominant_vector = np.abs(np.real(eigenvectors[:, index]))
centrality = dominant_vector / dominant_vector.sum()

nodes = ["A", "B", "C", "D"]
print("Dominant eigenvalue:", dominant_value)
for node, score in zip(nodes, centrality):
    print(f"{node}: {score:.4f}")

v = np.real(eigenvectors[:, index])
print("Verification error:",
      np.linalg.norm(A @ v - dominant_value * v))
```

Run it with:

```bash
python task_09.py
```
