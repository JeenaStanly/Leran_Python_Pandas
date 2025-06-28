If your file is a **Parquet** file instead of a CSV, you can use `pandas.read_parquet()` instead of `read_csv()`.

### ✅ Basic Syntax:

```python
import pandas as pd

df = pd.read_parquet('data.parquet')
print(df.head())
```

---

### 💡 Notes:

* Parquet is a **columnar** storage format — more efficient than CSV for both storage and speed.
* Requires either:

  * **`pyarrow`** or **`fastparquet`** backend installed.
  * You can install one like this:

    ```bash
    pip install pyarrow
    ```

    or

    ```bash
    pip install fastparquet
    ```

---

### 🧠 Comparing with `read_csv()`:

Many of the CSV options like `header`, `na_values`, or `parse_dates` are not needed because Parquet already stores metadata like:

* Column names
* Data types
* Missing values
* Date formats

So `read_parquet()` is often cleaner and faster:

```python
df = pd.read_parquet('data.parquet')  # Just this is often enough
```

---

### 📦 For S3 Parquet file:

```python
df = pd.read_parquet('s3://your-bucket/path/to/file.parquet', storage_options={
    'key': 'YOUR_AWS_ACCESS_KEY',
    'secret': 'YOUR_AWS_SECRET_KEY',
})
```

