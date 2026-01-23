## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-23 - Pandas Apply Performance Trap
**Learning:** Using `DataFrame.apply(axis=1)` for simple string manipulation creates significant overhead due to Series construction for each row. A list comprehension iterating over `zip()`ped columns was ~6.5x faster.
**Action:** Always replace row-wise `apply` with list comprehensions over `zip()` columns for simple element-wise operations.
