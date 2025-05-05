### Note: `google-re2` wheel building issue:

`pip` is probably using the **legacy `setup.py`** mechanism to build the wheel for `google-re2`, which is supposed to be deprecated in `pip` version 25.3.

To address this issue, you have a couple of options depending on your situation:

### ✅ Option 1: Use `--use-pep517` to Force the New Build System

You can try forcing the **PEP 517** build system, which is the newer, standardized way of building Python packages.

```bash
pip install --use-pep517 google-re2
```

If there are issues with build isolation, you can combine it with `--no-build-isolation`:

```bash
pip install --use-pep517 --no-build-isolation google-re2
```

---

### ✅ Option 2: Install the Latest Version of `pip`, `setuptools`, and `wheel`

Make sure your build tools are up-to-date to avoid any compatibility issues with older package formats. The newer versions of `pip` and `setuptools` might handle the build process better:

```bash
pip install --upgrade pip setuptools wheel
```

After upgrading, try installing `google-re2` again:

```bash
pip install google-re2
```

---

### ❌ Option 3: Avoid `google-re2` if It's Not Critical

If you are not using the **`google-re2`** package directly (i.e., it's a transitive dependency pulled in by another package), and you don't need it, you can try **skipping or excluding it**:

1. Uninstall any existing versions:

```bash
pip uninstall google-re2 -y
```

2. Install only the necessary dependencies without it:

```bash
pip install --no-deps apache-airflow-providers-apache-kafka
pip install kafka-python
```

This way, you avoid issues with `google-re2` entirely.
