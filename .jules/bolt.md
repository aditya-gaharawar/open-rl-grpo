## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-24 - Pandas Apply Performance
**Learning:** `DataFrame.apply(axis=1)` incurs significant overhead by creating a Series object for each row. For string manipulation tasks, using a list comprehension with `zip(df[col1], df[col2])` was measured to be ~6.6x faster.
**Action:** Replace `apply(axis=1)` with list comprehensions for simple row-wise transformations.

## 2024-05-25 - Hugging Face Dataset Column Access
**Learning:** Repeatedly accessing columns in a Hugging Face `Dataset` (e.g., `dataset['col']`) can trigger redundant data loading/decoding overhead. In filtering operations, extracting the column once into a NumPy array reduced execution time by ~48% (1.92x speedup) on 1M items.
**Action:** Extract dataset columns into a local variable (e.g., `arr = np.array(dataset['col'])`) before performing multiple operations like quantile calculation and filtering.
