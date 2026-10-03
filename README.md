# Exploratory-Data-Analysis-of-Used-Cars-in-India-
Exploratory Data Analysis of 8,000+ used-car listings from CarDekho: data cleaning, statistics and visualisation in Python (pandas, seaborn).
# Exploratory Data Analysis on Used Cars (CarDekho)

An end-to-end EDA project on a used-car listings dataset. It covers data inspection,
cleaning, descriptive statistics, visualisation and written insights, using Python only.
No machine-learning model is built.

## Dataset
**Vehicle Dataset from CarDekho** (`Car details v3.csv`), from Kaggle:
https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho

8,128 listings x 13 columns: name, year, selling price, km driven, fuel, seller type,
transmission, owner, mileage, engine, max power, torque, seats.
The CSV is not included in this repo. Download it from Kaggle and place it next to the notebook.

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
- Extracted `brand` from `name` (fixed "Land" and "Ashok" to Land Rover and Ashok Leyland)
- Stripped units (kmpl, km/kg, CC, bhp) and converted to numeric
- Treated impossible 0 values (mileage, max_power) as missing
- Filled ~3% missing values with the median within brand and fuel type
- Dropped `torque` (mixed, unparseable units)
- Removed 2 impossible `km_driven` records; kept luxury-car price outliers as real data

## Visualisations
Six charts of six types: histogram + KDE, bar plot, box plot, scatter plot (with hue),
violin plot and correlation heatmap. Each has a title, labelled axes and a written observation.

## Key findings
- Maruti and Hyundai make up 49.6% of listings.
- Prices are heavily right-skewed: mean Rs. 5.17 lakh vs median Rs. 4.00 lakh.
- Newer cars sell for more: median Rs. 6.55 lakh for cars up to 3 years old vs Rs. 1.60 lakh for cars 10+ years old.
- Automatics have a median about 2.2x the manual median, but they are also newer and more powerful.
- Max power is the strongest price correlate (r = 0.69); mileage is weak (r = -0.10).

## Limitations
No condition or accident history, no listing date (inflation and time effects are mixed in),
and a single platform dominated by mass-market brands with small samples for CNG, LPG and luxury cars.

## How to run
```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook StudentName_Cars_EDA_Project.ipynb
```
Keep `Car details v3.csv` in the same folder (or set `DATA_PATH` in the first cell), then choose Run All.

## Repo contents
- `StudentName_Cars_EDA_Project.ipynb`: full analysis notebook
- `StudentName_Cars_EDA_Report.pdf`: project report

## Author
VARUN D SAWALKAR
