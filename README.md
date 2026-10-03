# Exploratory Data Analysis on Used Cars (CarDekho)

An end-to-end EDA project on a used-car listings dataset: data inspection, cleaning,
descriptive statistics, visualisation and written insights, using Python only.
No machine-learning model is built.

## Dataset
**Vehicle Dataset from CarDekho** (`Car details v3.csv`), from Kaggle:
https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho

8,128 listings x 13 columns. The CSV is not included in this repo: download it from Kaggle
and place it in the same folder as the notebook.

## Questions explored
1. Which brands and fuel types are most common?
2. How are car prices distributed?
3. How do vehicle age, mileage and km driven relate to price?
4. Do automatic and manual cars differ in price?
5. Which features are most strongly correlated, and which brands are the most expensive?

## Cleaning summary
| Step | Rows | Columns |
|---|---|---|
| Raw data | 8,128 | 13 |
| After dropping duplicates | 6,926 | 13 |
| After final cleaning | 6,924 | 16 |

- Removed 1,202 exact duplicate rows
- Extracted `brand` from `name`; stripped units (kmpl, km/kg, CC, bhp) and converted to numeric
- Treated impossible 0 values (mileage, max_power) as missing; filled ~3% missing values with the median within brand and fuel type
- Dropped `torque` (mixed, unparseable units)
- Removed 2 impossible `km_driven` records; kept luxury-car price outliers as real data

## Visualisations
Six charts of six types: histogram + KDE, bar plot, box plot, scatter plot (with hue),
violin plot and correlation heatmap, each with a title, labelled axes and a written observation.

## Key findings
- Maruti and Hyundai make up 49.6% of listings.
- Prices are heavily right-skewed: mean Rs. 5.17 lakh vs median Rs. 4.00 lakh.
- Newer cars sell for more: median Rs. 6.55 lakh (up to 3 years old) vs Rs. 1.60 lakh (10+ years old).
- Automatics have a median about 2.2x the manual median, but they are also newer and more powerful.
- Max power is the strongest price correlate (r = 0.69); mileage is weak (r = -0.10).

## Limitations
No condition or accident history, no listing date (inflation and time effects are mixed in),
and a single platform dominated by mass-market brands, with small samples for CNG, LPG and luxury cars.

## How to run
```bash
pip install -r requirements.txt
jupyter notebook StudentName_Cars_EDA_Project.ipynb
```
Keep `Car details v3.csv` next to the notebook (or set `DATA_PATH` in the first code cell), then choose Run All.

## Repo contents
- `StudentName_Cars_EDA_Project.ipynb` - analysis notebook
- `StudentName_Cars_EDA_Report.pdf` - project report
- `requirements.txt` - Python libraries needed

## Author
VARUN D SAWALKAR
