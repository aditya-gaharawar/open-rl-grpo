## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-23 - Batch Tokenization in Notebooks
**Learning:** Pandas `apply` combined with tokenizer calls is a massive performance bottleneck. Using `tokenizer.apply_chat_template` in batch mode (passing a list of conversations) is significantly faster (10x+) than row-wise iteration.
**Action:** Replace `df.apply(lambda x: len(tokenizer(x)))` with `tokenizer(df.tolist())` whenever possible.
