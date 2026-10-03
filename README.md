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

  ## insights

  <img width="1194" height="526" alt="image" src="https://github.com/user-attachments/assets/3d279c0e-ed3b-408c-ac5f-54fd076dcfd8" />
<img width="1016" height="581" alt="image" src="https://github.com/user-attachments/assets/b58be48e-efda-4878-8108-3362c4a5a6fb" />
<img width="1207" height="584" alt="image" src="https://github.com/user-attachments/assets/47523add-294d-4ada-b099-10de799e1bd9" />
<img width="1216" height="643" alt="image" src="https://github.com/user-attachments/assets/48e5356d-2ee1-4888-8743-13053b2cc6e8" />
<img width="884" height="534" alt="image" src="https://github.com/user-attachments/assets/0e589419-389c-4474-8349-16acf13a292d" />
Observation: Diesel cars have the highest median price (Rs. 5.20 lakh) followed by Petrol (Rs. 3.10 lakh); CNG (3.20) and LPG (1.96) are the cheapest.
CNG (56) and LPG (38) have very few records, so their shapes are indicative only. Diesel also has the longer upper tail (95th percentile Rs. 15.7 lakh vs Rs. 7.8 lakh for petrol).
<img width="826" height="684" alt="image" src="https://github.com/user-attachments/assets/59b91a6f-d635-435f-89fb-4602232da2dd" />
Observation: Price correlates most strongly with max_power (0.69), year (0.43) and engine (0.44); km_driven (-0.20) and mileage (-0.10) are negative.
Engine and max_power are highly inter-correlated (0.68), and year is negatively related to km_driven (-0.44), i.e. newer cars tend to have fewer kilometres.


-------------------------------------------------------------

==============================================================================
KEY FINDINGS
==============================================================================
1. Market is concentrated: Maruti and Hyundai hold 49.6% of listings; diesel (54.2%) and petrol (44.4%) cars make up almost everything.
2. Prices are right-skewed: mean Rs. 5.17 lakh vs median Rs. 4.00 lakh (skewness 5.57 -> -0.16 after log).
3. Newer cars sell for more: car age is negatively correlated with price (r = -0.43); median price is Rs. 6.55 lakh for cars <= 3 years old vs Rs. 1.60 lakh for cars >= 10 years old.
4. Automatic cars cost about 2.2x the manual median (Rs. 8.50 vs Rs. 3.85 lakh) - but they are newer (median year 2016 vs 2014) and more powerful, so this is association, not proof of a gearbox premium.
5. Power is the strongest price correlate (max_power r = 0.69); mileage is only weakly (negatively) related (r = -0.10). Highest average prices belong to BMW, Audi, Mercedes-Benz, far above Maruti (Rs. 3.88 lakh average).

Limitations: (1) no accident/service history or exact condition, (2) listings are spread over many years with no listing date, so inflation and time effects are mixed in, (3) data comes from one platform and mostly Indian mass-market cars, so results may not generalise; CNG, LPG and luxury brands have small samples.





## Author
VARUN D SAWALKAR
