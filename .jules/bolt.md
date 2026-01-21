## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2025-05-23 - Pandas Apply Bottleneck
**Learning:** `DataFrame.apply(axis=1)` creates a Series object for every row, which incurs significant overhead for simple string manipulation or formatting tasks. This is a common bottleneck in data preparation cells.
**Action:** Replace row-wise `apply` with list comprehensions iterating over `zip()` of the required columns. This avoids Series creation and can yield ~2x-100x speedups depending on the operation complexity.
