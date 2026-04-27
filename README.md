# HW4
---


## Cloning the repository
1. Go somewhere outside your current project:
   a. cd ~

2. Clone into a test folder
   a. git clone https://github.com/SebastianKou/HW4.git test-clone

3. Enter it and make sure it copied over
   a. cd test-clone
   b. ls
   
## Data

The `data` folder contains the merged panel dataset built from raw HCRIS cost report files. **You must build this dataset before running the notebook.** Run the following scripts in order:

1. `HW1-data` — 
2. `HW2-data` —
3. `hcris-full` — produces the final `data-*.csv` files used in the notebook

The notebook loads all CSV files with:
```python
import glob
files = glob.glob('../HW4/data/output/data-*.csv')
data = pd.concat((pd.read_csv(f) for f in files), ignore_index=True)
```
> ⚠️ Make sure the relative path `../HW4/data/output/` matches your local directory structure, or update the glob path accordingly.

---


## Key Variable Definitions

- **`net_penalty`** = `hrrp_payment + hvbp_payment` (negative = penalized under VBP)
- **`price`** = `(ip_charges + icu_charges + ancillary_charges) × discount_factor − tot_mcare_payment) / (tot_discharges − mcare_discharges)`
- **`discount_factor`** = `1 − tot_discounts / tot_charges`
- **Instrument** = avg. Medicare discharges per hospital, 2009–2011
- Outliers trimmed at the 1st and 99th percentile within each year

---

