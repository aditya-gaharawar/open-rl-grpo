## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-24 - Efficient Tokenization in Notebooks
**Learning:** When calculating token lengths for a DataFrame column in a notebook, using `tokenizer.apply_chat_template(list_of_conversations, tokenize=True)` is significantly faster (observed ~4x speedup) than using `df.apply()` row-wise. Tokenizers are often optimized for batch processing.
**Action:** Replace row-wise tokenization/length checks with batch tokenization via list comprehensions: `[len(x) for x in tokenizer.apply_chat_template(df["col"].tolist(), tokenize=True)]`.
