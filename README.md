# Unit 3 – Multimedia and Interactive Visualization

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![VS Code](https://img.shields.io/badge/VS%20Code-Supported-007ACC?logo=visualstudiocode&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-Interactive-3F4F75?logo=plotly&logoColor=white)

**Course:** UE24CS342AA9

Unit 3 activities for *Multimedia and Interactive Visualization*. The notebooks cover data visualization, multimedia processing, temporal analysis, and interactive visualization using Python. They are adapted to run **locally in VS Code**, with no dependency on Google Colab or Google Drive paths.

## Table of Contents

- [Activities](#activities)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Dataset Setup](#dataset-setup)
- [Running the Notebooks](#running-the-notebooks)
- [Troubleshooting](#troubleshooting)
- [Project Structure](#project-structure)
- [Notes](#notes)

## Activities

| Notebook | Focus |
|----------|-------|
| **PPT 1** | Multimedia and CCTV log analysis, image processing, and audio signal analysis |
| **PPT 3** | Visualization activities and associated data analysis |
| **PPT 5** | Temporal data visualization and analysis |
| **PPT 7** | Interactive visualization, linked views, and exploration of flagged cases |

Each notebook contains its own tasks, code, and reflection questions.

## Tech Stack

- Python 3.12
- NumPy
- Pandas
- Matplotlib
- SciPy
- Plotly
- IPython
- Jupyter Notebook
- nbformat
- KaggleHub (where required for dataset access)

## Prerequisites

1. Python 3.12 (or a compatible version)
2. [Visual Studio Code](https://code.visualstudio.com/)
3. VS Code extensions:
   - **Python**
   - **Jupyter**
4. The datasets required by the individual activities (see [Dataset Setup](#dataset-setup))

## Getting Started

### 1. Open the project

Open the project folder in VS Code, or navigate to it from your terminal:

```bash
cd ~/Desktop/vdui
```

### 2. Create a dedicated Conda environment

```bash
conda create -n vdui python=3.12 -y
conda activate vdui
```

If the environment already exists, just activate it:

```bash
conda activate vdui
```

### 3. Install dependencies

```bash
python -m pip install numpy pandas matplotlib scipy plotly ipython ipykernel nbformat kagglehub
```

Register the environment as a Jupyter kernel:

```bash
python -m ipykernel install --user --name vdui --display-name "Python (VDUI)"
```

### 4. Select the kernel in VS Code

1. Open the required `.ipynb` notebook.
2. Click the kernel selector in the upper-right corner.
3. Choose **Python (VDUI)** or the interpreter belonging to the `vdui` environment.
4. Restart the kernel if necessary.
5. Run the cells in order.

> [!IMPORTANT]
> Use the same Python environment for installing packages and running the notebooks.

## Dataset Setup

Some activities require external CSV files. Keep them in the project directory, or update the paths in the relevant notebooks. Check the first setup cells of each notebook for the exact filenames.

For example, **PPT 1** expects:

```text
unit3_ppt1_cctv_log.csv
```

Configure a local path with:

```python
from pathlib import Path

DATA_DIR = Path.cwd()
data_path = DATA_DIR / "unit3_ppt1_cctv_log.csv"
```

Verify the file exists before loading it:

```python
print("Dataset exists:", data_path.exists())
```

If this prints `False`, place the correct CSV in the expected directory or change `DATA_DIR` to point to the folder containing it.

> [!WARNING]
> Do not rename a dataset to match an expected filename unless it actually contains the expected data and columns.

## Running the Notebooks

1. Open the required notebook.
2. Select the **Python (VDUI)** kernel.
3. Run the setup cells first.
4. Confirm all required datasets are available.
5. Execute the remaining cells in order.
6. Review the generated plots, interactive visualizations, and reflection answers.

> [!NOTE]
> Files ending in `.ipynb` must be opened with the Jupyter extension in VS Code. Do not run notebook JSON files as ordinary Python scripts.

## Troubleshooting

<details>
<summary><strong>NumPy / Pandas dependency conflicts</strong></summary>

Use the dedicated `vdui` environment rather than installing into the Conda `base` environment, so packages don't conflict with other projects.

</details>

<details>
<summary><strong>Plotly rendering error</strong></summary>

If you see:

```text
ValueError: Mime type rendering requires nbformat>=4.2.0 but it is not installed
```

install the dependencies with the active interpreter:

```bash
python -m pip install --upgrade nbformat ipython plotly
```

Then restart the notebook kernel and rerun the cells.

</details>

<details>
<summary><strong>Missing dataset (<code>FileNotFoundError</code>)</strong></summary>

Check the filename and working directory:

```python
from pathlib import Path

print("Current directory:", Path.cwd())
print("Available files:", [p.name for p in Path.cwd().iterdir()])
```

Place the required dataset in the correct folder or update its path.

</details>

<details>
<summary><strong>Kernel or package mismatch</strong></summary>

Check which interpreter is running:

```python
import sys
print(sys.executable)
```

The path should point to the `vdui` environment, not the Conda `base` interpreter.

</details>

<details>
<summary><strong><code>NameError: name 'null' is not defined</code></strong></summary>

This happens when a notebook's raw JSON is executed as Python. Open `.ipynb` files as notebooks in VS Code instead.

</details>

## Project Structure

```text
vdui/
├── unit3_ppt1_activity_PES2UG24CS252_VSCode.ipynb
├── unit3_ppt3_activity_PES2UG24CS252_VSCode.ipynb
├── Unit3_PPT5_Temporal_Activity_PES2UG24CS252_VSCode.ipynb
├── unit3_ppt7_activity_PES2UG24CS252_VSCode.ipynb
├── unit3_ppt1_cctv_log.csv
├── README.md
└── .gitignore
```

Additional notebooks, datasets, and supporting files may be present depending on the activity.

## Notes

- Run cells in order; later cells may depend on variables created earlier.
- Keep required datasets alongside the notebooks where appropriate.
- Large datasets may not be included in the repository and may need to be obtained separately.
- Interactive Plotly charts are best viewed in the notebook output area.
- Don't commit virtual environments, cache folders, or large datasets unless explicitly required.

## Summary

These activities run locally with VS Code, Python, and Jupyter. A dedicated Python environment and correctly configured dataset paths ensure reproducible execution across the Unit 3 notebooks.

