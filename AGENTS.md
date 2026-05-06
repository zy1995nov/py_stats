# AGENTS.md

## Cursor Cloud specific instructions

This repository is a data science / statistical analysis project containing a single Jupyter notebook (`独立样本T检验/调参.ipynb`) that performs Independent Samples T-Tests.

### Key notes

- **Hardcoded path**: The notebook's data-loading cell uses an absolute path (`/Users/zhangyu/Desktop/统计学算法/独立样本T检验/实验数据.xlsx`). When running the notebook programmatically, override this to the relative path `实验数据.xlsx` (run from the `独立样本T检验/` directory).
- **Running as root**: Jupyter must be started with `--allow-root` in this environment.
- **Dependencies**: `pandas`, `numpy`, `scipy`, `openpyxl`, `jupyter` (installed via pip).

### Running the notebook

```bash
cd /workspace/独立样本T检验
jupyter notebook --no-browser --ip=0.0.0.0 --port=8888 --ServerApp.token="" --ServerApp.password="" --allow-root
```

### Executing the notebook non-interactively

```bash
cd /workspace/独立样本T检验
python3 -c "
import nbformat
from nbclient import NotebookClient

with open('调参.ipynb', 'r') as f:
    nb = nbformat.read(f, as_version=4)

for cell in nb.cells:
    if cell.cell_type == 'code' and '/Users/zhangyu/Desktop/' in cell.source:
        cell.source = cell.source.replace(
            r\"/Users/zhangyu/Desktop/统计学算法/独立样本T检验/实验数据.xlsx\",
            \"实验数据.xlsx\"
        )

client = NotebookClient(nb, timeout=60, kernel_name='python3')
client.execute()
"
```

### Linting

No project-level linter is configured. Basic validation can be done by verifying the notebook is valid JSON and executing all code cells without errors.
