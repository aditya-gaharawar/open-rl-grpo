## 2024-05-22 - Notebook Cell Independence
**Learning:** In Jupyter Notebooks, relying on global imports from previous cells is fragile for batched operations or complex logic introduced in later cells. Always re-import critical modules (like `sys`, `subprocess`) inside the optimized cell to ensure it works even if the kernel state is inconsistent or cells are run out of order.
**Action:** When optimizing notebook cells, explicitly import dependencies within the cell if they are crucial for the optimization logic.

## 2024-05-24 - Pandas Apply Performance
**Learning:** `DataFrame.apply(axis=1)` incurs significant overhead by creating a Series object for each row. For string manipulation tasks, using a list comprehension with `zip(df[col1], df[col2])` was measured to be ~6.6x faster.
**Action:** Replace `apply(axis=1)` with list comprehensions for simple row-wise transformations.

## 2024-05-27 - HuggingFace Tokenizer Optimization
**Learning:** `tokenizer.apply_chat_template(tokenize=True)` performs both Jinja2 template rendering and tokenization. If you also need the formatted text (e.g. for the dataset column), calling `apply_chat_template(tokenize=False)` separately doubles the rendering cost.
**Action:** Generate the text column first using `tokenize=False`, then tokenize the resulting text to get lengths. This eliminates one pass of Jinja2 rendering.
