## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-24 - Pandas Apply Performance
**Learning:** `DataFrame.apply(axis=1)` incurs significant overhead by creating a Series object for each row. For string manipulation tasks, using a list comprehension with `zip(df[col1], df[col2])` was measured to be ~6.6x faster.
**Action:** Replace `apply(axis=1)` with list comprehensions for simple row-wise transformations.

## 2024-05-27 - Chat Template Optimization
**Learning:** `tokenizer.apply_chat_template(..., tokenize=True)` performs both template rendering and tokenization. When both the formatted text string and its token length are required, calling `apply_chat_template` twice (once for text, once for lengths) duplicates the expensive Jinja2 rendering work. Benchmarking showed that generating text once and then tokenizing it (`tokenizer(text)`) is ~1.7x faster.
**Action:** Generate formatted text first using `apply_chat_template(tokenize=False)`, then tokenize the resulting strings to get lengths.
