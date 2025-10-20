# EmergencyBloodDelivery_DataGen_Repo

This canvas contains a ready-to-copy GitHub-style repository for the data generation described in your README.docx. It includes a Python script `instance_gen.py`, a small `utils.py`, a `requirements.txt`, a `.gitignore`, and an example `README.md` (converted). Copy the file contents into your repo and run `instance_gen.py` to reproduce the data sampling process.

---

## File tree

```
EmergencyBloodDelivery_DataGen_Repo/
├── README.md
├── instance_gen.py
├── utils.py
├── requirements.txt
├── .gitignore
└── data/
    └── dhaka_random_locations.csv   # keep this in the same folder as the code (or provide path)
```

---

## README.md

````markdown
# Data Generation for Emergency Blood Delivery (Two-Echelon, Post-Earthquake Megacity)

This repository generates synthetic data used in the study "Emergency Blood Delivery in a Post-Earthquake Megacity with a Two-Echelon System".

**Python version:** 3.13.0

**Required packages:** pandas

## How to reproduce

1. Place `dhaka_random_locations.csv` inside the `data/` folder (or provide a path).
2. Edit or run `instance_gen.py`.

Example usage:

```bash
python instance_gen.py --locations data/dhaka_random_locations.csv --out-dir output --n-instances 50
````

The script will generate one or more CSV files containing sampled instances.

Notes:

* Input file names, output file names and output paths can be user-specified through command-line arguments.
* You should specify the number of samples to generate.

```
```

````

---

## requirements.txt

```text
pandas>=2.0
````

---

## .gitignore

```text
__pycache__/
output/
*.pyc
.env
```

---

## utils.py

```python
"""
Utility functions for instance generation.
"""
import pandas as pd
import random
from typing import Tuple, List


def load_locations(path: str) -> pd.DataFrame:
    """Load location file with at least columns: name, latitude, longitude.

    Args:
        path: path to CSV file

    Returns:
        pandas.DataFrame
    """
    df = pd.read_csv(path)
    # Try to tolerate common column name variants
    lower_cols = {c.lower(): c for c in df.columns}
    col_map = {}
    for key in ("name", "hospital", "hospital_name"):
        if key in lower_cols:
            col_map[lower_cols[key]] = "name"
            break
    for key in ("lat", "latitude"):
        if key in lower_cols:
            col_map[lower_cols[key]] = "latitude"
            break
    for key in ("lon", "longitude", "long"):
        if key in lower_cols:
            col_map[lower_cols[key]] = "longitude"
            break
    df = df.rename(columns=col_map)
    required = ["name", "latitude", "longitude"]
    missing = [c for c in required if c not in df.columns]
    if missing:
        raise ValueError(f"Missing required columns in locations file: {missing}")
    return df[["name", "latitude", "longitude"]]


def generate_demands(n: int, mean: float = 50, std: float = 15, seed: int | None = None) -> List[int]:
    """Generate a list of integer demands for n hospitals.

    Args:
        n: number of hospitals
        mean: mean demand
        std: standard dev
```




