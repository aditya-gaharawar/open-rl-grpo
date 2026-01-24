## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-23 - Notebook Code Validation
**Learning:** When optimizing Jupyter Notebook cells programmatically, verifying the syntax of the modified cell using `ast.parse()` is a crucial step to prevent introducing syntax errors that would only be caught at runtime (often requiring a GPU session).
**Action:** Always include a validation script that extracts and parses the modified cell code when editing notebooks.
