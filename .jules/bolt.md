## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-24 - Pandas Apply Performance
**Learning:** `DataFrame.apply(axis=1)` incurs significant overhead by creating a Series object for each row. For string manipulation tasks, using a list comprehension with `zip(df[col1], df[col2])` was measured to be ~6.6x faster.
**Action:** Replace `apply(axis=1)` with list comprehensions for simple row-wise transformations.

## 2024-05-25 - HF Dataset Column Access
**Learning:** Accessing a column in a Hugging Face Dataset (e.g., `dataset["col"]`) triggers data loading and list construction each time. For operations like filtering based on statistics (e.g., quantile + select), accessing the column twice is inefficient.
**Action:** Extract the column data into a variable (e.g., NumPy array) once and reuse it for subsequent operations to avoid redundant data loading.
