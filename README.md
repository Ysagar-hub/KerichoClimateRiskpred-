Author: Sagar Kumar

KerichoClimateRiskpred is a Python project that estimates climate risk for agriculture in Kericho, Kenya using daily weather data from the NASA POWER API (2010 to present). The script identifies common weather hazards, combines them into a Climate Risk Index (CRI), and uses that index to approximate crop loss and economic impact. It also labels each year into a simple risk category (low/medium/high), calculates an example insurance premium, and trains a Random Forest model to predict yearly risk levels. Finally, it produces graphs showing CRI trends, estimated losses, and hazard importance.

Location and data source
Location: Kericho, Kenya
Latitude: -0.367
Longitude: 35.283

Data source: NASA POWER (daily data for a single point)

Variables used:

T2M (average temperature)
T2M_MAX (maximum temperature)
T2M_MIN (minimum temperature)
PRECTOTCORR (precipitation)
WS2M (wind speed)
RH2M (relative humidity)
What the script does (step-by-step)
Downloads daily weather data from NASA POWER.
Cleans the dataset by replacing -999 with missing values and filling gaps.
Creates hazard indicators:
heavy rain (precipitation > 50 mm/day)
dry day (precipitation < 1 mm/day)
dry spell (7 consecutive dry days)
heat stress (max temperature > 32°C)
high wind (wind speed > 6 m/s)
Detects hail events using a rule-based proxy (rain + cold minimum temperature + wind + high humidity).
Builds a daily CRI score using weighted hazards, then aggregates it to an annual CRI (scaled 0–100).
Estimates crop loss percentage and converts it into economic loss using farm area and value per hectare.
Assigns a yearly risk class (LOW, MEDIUM, HIGH) and calculates an example insurance premium.
Trains a Random Forest model using annual hazard totals to predict the yearly risk class.
Saves results to CSV files and creates plots for CRI, loss trends, and feature importance.
How to run
Install dependencies:

pip install -r requirements.txt

Run the script:

python your_script_name.py

Replace your_script_name.py with whatever you saved the file as.

Output files
CSV outputs:

step1_raw_weather.csv
step2_clean_weather.csv
step3_hazards.csv
step4_hail_events.csv
step5_annual_cri.csv
step6_economic_loss.csv
step7_insurance_report.csv
step8_feature_importance.csv
Graphs:

graph_cri.png
graph_loss.png
graph_feature_importance.png
Notes
Hail detection is a proxy method and should be validated with real hail observations if you plan to use it beyond a demonstration. Crop loss and insurance premium calculations are simplified examples and are not intended to be treated as official pricing or actuarial results.
