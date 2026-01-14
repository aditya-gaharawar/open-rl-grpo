## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-22 - Batched Tokenization in Datasets
**Learning:** Using `tokenizer.apply_chat_template(tokenize=True)` inside a list comprehension is slow because it calls the tokenizer (which is often Rust-backed and optimized for batches) sequentially in Python.
**Action:** Unroll the loop: first apply the template with `tokenize=False` to get a list of strings (fast string ops), then call `tokenizer(list_of_strings)` once. This leverages the tokenizer's internal parallelism and Rust backend, yielding significant speedups for large datasets.
