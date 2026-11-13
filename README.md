# Prairie-Crop-Tracker-Do-Wet-Junes-Hurt-Crop-Yields
A data pipeline analyzing the relationship between June rainfall and corn yields in Lyon County, Minnesota, from 2000 to 2022.
# Prairie Crop Tracker: Lyon County, Minnesota

## Project Question

Do wet or dry Junes affect corn yields in Lyon County, Minnesota?

## Study Area

- **County:** Lyon County
- **State:** Minnesota
- **Crop:** Corn for grain
- **Yield measurement:** Bushels per acre
- **Study Period:** 2000–2022
- **Number of Observations:** 23 years

## Data Sources

- [USDA NASS Quick Stats API](https://quickstats.nass.usda.gov/api/) – Historical county-level corn yield data.
- [Open-Meteo Historical Weather API](https://archive-api.open-meteo.com/v1/archive) – Historical precipitation and temperature data.

## Data Pipeline

Extract → Transform → Combine → Load → Analyze

1. Extract historical corn yield data from the USDA NASS Quick Stats API.
2. Extract historical weather data from Open-Meteo.
3. Clean the datasets, convert yield values to numeric data, and handle missing values.
4. Aggregate daily weather data into yearly measurements.
5. Combine crop yields and weather data using the year.
6. Load cleaned data into CSV and SQLite.
7. Analyze yield trends and compare yield anomalies across rainfall categories.

## Key Findings

### Yield Trend

Corn yields generally increased between 2000 and 2022. The linear trend showed an average increase of approximately **1.845 bushels per acre per year**.

### June Rainfall Categories

| Category | Years | Average Yield (bu/acre) | Average June Rainfall (in) | Average Yield Anomaly (bu/acre) |
|---|---:|---:|---:|---:|
| Dry | 6 | 163.10 | 2.11 | -8.55 |
| Normal | 11 | 171.73 | 4.21 | +10.23 |
| Wet | 6 | 155.30 | 7.45 | -10.20 |

Normal June rainfall years had the highest average yield and average yield anomaly. Wet June years had the lowest average yield.

### Worst Yield Years

The three worst years based on yield anomaly were:

- **2021:** -20.84 bushels per acre, with 1.193 inches of June rainfall (Dry).
- **2013:** -18.78 bushels per acre, with 6.114 inches of June rainfall (Wet).
- **2014:** -18.33 bushels per acre, with 11.248 inches of June rainfall (Wet).

These results suggest that both unusually dry and wet June conditions can be associated with lower-than-trend corn yields.

## Charts

The project includes three visualizations:

1. Corn yield by year with a linear trend line.
   <img width="1189" height="590" alt="corn_yield" src="https://github.com/user-attachments/assets/f3bce999-803a-401b-b118-3029f9d6775c" />

2. June rainfall by year, categorized as dry, normal, or wet.
   <img width="1189" height="590" alt="june_rainfall" src="https://github.com/user-attachments/assets/0a381a3b-e47a-40ec-b915-ac11af2261af" />

3. June rainfall against yield anomaly, with rainfall categories identified.
   <img width="989" height="590" alt="rainfall_yield_anomaly" src="https://github.com/user-attachments/assets/38289e21-5f08-41a2-8311-697977e5e40b" />


![Corn Yield Trend](charts/corn_yield_trend.png)

## Limitations

- The analysis covers only 23 years of observations from one county.
- Rainfall measurements are historical weather estimates from Open-Meteo rather than direct measurements from every farm.
- Corn yields are affected by other factors, including soil conditions, temperature, farming practices, pests, and seed varieties.
- A relationship between rainfall and yield does not establish that rainfall alone caused changes in crop production.
- Yield anomalies are calculated relative to a linear trend, which may not capture every long-term change in agricultural productivity.

## Reproducibility

The project was developed using Python in Google Colab.

**[Open Notebook in Google Colab](https://colab.research.google.com/drive/1OE6M3CVa225b7v53gCDwpJAX2JZA4OJm?usp=sharing)**

Libraries used:
- requests
- pandas
- matplotlib
- numpy
- sqlite3
- json
- datetime

## Attribution

**Corn Yield Data**

Data provided by the [United States Department of Agriculture (USDA), National Agricultural Statistics Service (NASS)](https://www.nass.usda.gov/).

Data retrieved through the [NASS Quick Stats Database](https://quickstats.nass.usda.gov/), using the [Quick Stats API](https://quickstats.nass.usda.gov/api/).

**Historical Weather Data**

Weather data provided by [Open-Meteo](https://open-meteo.com/), using the [Historical Weather API](https://open-meteo.com/en/docs/historical-weather-api).

Open-Meteo API data is provided under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

Weather data was retrieved, processed, and aggregated for this project. The resulting dataset and visualizations are derived from the original API data.

## Author

Don Huynh

### AI Use Note

I used ChatGPT to help understand the assignment, troubleshoot Python code, and organize parts of the data analysis. I ran the code in Google Colab and used the results from my own datasets to interpret the findings.
