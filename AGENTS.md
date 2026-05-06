## Cursor Cloud specific instructions

### Overview

This is a Python data-science notebook repository (`py_stats`) containing a Jupyter notebook for independent samples T-test analysis. There is no build system, no test framework, and no linting configuration.

### Services

| Service | Command | Notes |
|---------|---------|-------|
| Jupyter Notebook | `jupyter notebook --ip=0.0.0.0 --port=8888 --no-browser --allow-root --NotebookApp.token="" --NotebookApp.password=""` | Serves the notebook UI |

### Dependencies

Python packages: `pandas`, `numpy`, `scipy`, `openpyxl`, `jupyter`. Installed via pip (no `requirements.txt` in repo).

### Non-obvious caveats

- The notebook `独立样本T检验/调参.ipynb` hardcodes a data file path at `/Users/zhangyu/Desktop/统计学算法/独立样本T检验/实验数据.xlsx`. The actual data file is at `/workspace/独立样本T检验/实验数据.xlsx`. A symlink must be created for the notebook to run without code modification:
  ```
  mkdir -p /Users/zhangyu/Desktop/统计学算法/独立样本T检验
  ln -sf /workspace/独立样本T检验/实验数据.xlsx /Users/zhangyu/Desktop/统计学算法/独立样本T检验/实验数据.xlsx
  ```
- To execute the notebook programmatically (headless): `jupyter nbconvert --to notebook --execute "独立样本T检验/调参.ipynb" --ExecutePreprocessor.timeout=120`
- There are no tests or linting tools configured in this repo.
