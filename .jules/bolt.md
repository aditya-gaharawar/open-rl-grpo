## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-22 - Pandas Apply vs List Comprehension
**Learning:** `DataFrame.apply(axis=1)` is significantly slower than list comprehensions with `zip()` for row-wise string operations because `apply` creates a Series object for every row.
**Action:** Replace `apply(axis=1)` with `[func(x, y) for x, y in zip(df['A'], df['B'])]` when doing simple row-wise transformations. Observed 6x speedup.
