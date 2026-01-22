## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-23 - Pandas Filtering Pitfalls
**Learning:** When filtering Pandas DataFrames (e.g., via boolean masking), the original index is preserved. Accessing rows by label (e.g., `df['col'][0]`) will raise a KeyError if the row with label 0 was filtered out.
**Action:** Always use positional indexing `.iloc[0]` when accessing the "first" element of a filtered DataFrame for validation or examples.
