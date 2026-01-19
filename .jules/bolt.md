## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-24 - Pandas Apply vs List Comprehension
**Learning:** `DataFrame.apply(axis=1)` for string formatting is significantly slower (~5x) than list comprehension with `zip` due to the overhead of creating Series objects for each row.
**Action:** Replace `apply` with list comprehensions when performing row-wise string manipulation or simple logic on DataFrames.
