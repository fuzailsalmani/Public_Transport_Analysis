# 🚌 Public Transportation Analytics

> **A Python, Exploratory Data Analysis (EDA), and Power BI project
> using a synthetic, GTFS-inspired public transportation dataset.**\
> Explore passenger demand, service reliability, delays, vehicle
> occupancy, route performance, temporal patterns, anomalies, and
> data-quality flags across five cities.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge)
![Power
BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Project-Completed-14B8A6?style=for-the-badge)

------------------------------------------------------------------------

## 👋 About the Project

**Public Transportation Analytics** explores trip-level public
transportation data across London, Paris, Berlin, Tokyo, and New York.
The project uses Python for data inspection, cleaning, data-quality
investigation, and exploratory analysis, followed by a six-page Power BI
report.

The analysis focuses on passenger demand, route types, service status,
delays, vehicle occupancy, capacity, weather conditions, time-based
patterns, and recorded anomaly categories. The data-quality work also
checks related fields for potential inconsistencies and keeps
investigation flags separate from the original values.

> **Dataset context:** The dataset is synthetic and GTFS-inspired. The
> findings in this repository describe this dataset only; they are not
> verified measurements of the actual public transportation systems in
> these cities.

## 🎯 Project Objectives

-   Inspect the dataset structure, column types, completeness,
    uniqueness, and value ranges.
-   Prepare a separate working copy and convert the timestamp field to
    datetime.
-   Investigate passenger, boarding, occupancy, service-status, delay,
    and cancellation fields.
-   Add transparent flags for two potential data-quality patterns
    without silently changing the source values.
-   Explore passenger demand by city, route type, hour, and day of week.
-   Analyze service reliability, delays, cancellations, occupancy, and
    vehicle capacity.
-   Examine weather-related delay patterns and recorded anomaly
    categories.
-   Build an interactive Power BI report with six analytical pages.

## 🧰 Tools & Technologies

  -----------------------------------------------------------------------
  Tool                                How it is used
  ----------------------------------- -----------------------------------
  Python                              Data preparation, validation, and
                                      analysis

  Pandas                              Data inspection, cleaning,
                                      grouping, and calculations

  NumPy                               Numerical operations

  Matplotlib                          Charts and visual exploration

  Seaborn                             Statistical plots and distributions

  Jupyter Notebook                    Notebook-based workflow

  Power BI                            Interactive report, KPI cards,
                                      charts, matrices, and slicers

  DAX                                 Measures and filter-responsive
                                      report calculations
  -----------------------------------------------------------------------

## 🗂️ Repository Structure

``` text
Public-Transportation-Analytics/
├── README.md
├── data/
│   └── processed/
│       └── public_transportation_cleaned.csv
├── notebooks/
│   ├── Public_Transportation_Data_Cleaning.ipynb
│   └── Public_Transportation_EDA.ipynb
├── powerbi/
│   └── Public_transport.pbix
├── screenshots/
│   ├── executive_overview.png
│   ├── city_intelligence.png
│   ├── service_reliability.png
│   ├── passenger_demand.png
│   ├── fleet_efficiency.png
│   └── anomaly_detection.png
└── requirements.txt
```

> 📝 The folder and screenshot names above are the proposed repository
> layout confirmed for this project. The cleaned CSV was not included
> with the files supplied for preparing this README. Add it to
> `data/processed/` if you intend to publish the prepared dataset. The
> raw source dataset is also not included here.

## 🔬 Analysis Workflow

### 1. 🔍 Data Understanding & Initial Inspection

Notebook: `Public_Transportation_Data_Cleaning.ipynb`

-   Load the source CSV and inspect sample records, dataset dimensions,
    column names, and data types.
-   Review numerical and categorical summaries.
-   Check missing values, duplicate rows, unique trip IDs, and timestamp
    values.
-   Inspect numeric ranges, occupancy values, and binary indicator
    fields.
-   Review passenger counts, boarding and alighting counts, vehicle
    capacity, and service-related fields.

### 2. 🧹 Data Cleaning & Data-Quality Investigation

Notebook: `Public_Transportation_Data_Cleaning.ipynb`

-   Keep the original DataFrame unchanged and create a separate working
    copy.
-   Convert `timestamp` to datetime.
-   Check timestamp validity and the date range.
-   Compare `occupancy_rate` with `passenger_count / vehicle_capacity`.
-   Check consistency between `cancellation_flag` and `service_status`.
-   Investigate records where `boarding_count > 0` while
    `passenger_count == 0`.
-   Investigate potential inconsistencies between `service_status` and
    `delay_minutes`.
-   Preserve source values and add two integer flags for further
    analysis:
    -   `boarding_passenger_mismatch`
    -   `status_delay_mismatch`
-   Export the prepared dataset separately from the source file.

**Data-quality audit results**

  Check                                                            Result
  ---------------------------------------------------- ------------------
  Total records                                                   500,000
  Original columns before adding investigation flags                   31
  Columns in the prepared dataset                                      33
  Missing values                                                        0
  Duplicate rows                                                        0
  Duplicate trip IDs                                                    0
  Invalid timestamps                                                    0
  Boarding/passenger potential mismatch                    46,333 (9.27%)
  Status/delay potential mismatch                        129,307 (25.86%)
  Cancellation flag mismatches                                          0

The two mismatch flags identify records for review under the rules used
in the notebook. They do not prove which source field is incorrect. The
original values were retained.

### 3. 📊 Exploratory Data Analysis

Notebook: `Public_Transportation_EDA.ipynb`

The EDA notebook follows a sequence of dataset overview, univariate
analysis, bivariate analysis, multivariate analysis, time-based
analysis, and written observations.

Areas explored include:

-   City-wise and route-type record distributions.
-   Service status, fare type, weather condition, anomaly type, and
    day-of-week distributions.
-   Passenger-count, delay, occupancy, temperature, travel-time,
    vehicle-capacity, route-length, and headway distributions.
-   Passenger count and occupancy by route type and city.
-   Average delay by city, route type, and hour.
-   Scheduled versus actual travel time by route type.
-   Delay distribution by service status.
-   Service-status distribution and cancellation rate by city.
-   Delay rate by weather condition.
-   Average passenger count by hour and day of week.
-   Numerical correlation heatmap.
-   Passenger count versus occupancy rate using a 10,000-row sample.

### 4. 📈 Power BI Dashboard

The Power BI report contains six pages:

1.  **Executive Overview** --- high-level transportation KPIs and an
    overall view of the dataset.
2.  **City Intelligence** --- city-level comparisons and network-related
    analysis.
3.  **Service Reliability** --- service status, delays, and reliability
    analysis.
4.  **Passenger Demand** --- passenger activity and time-based demand
    patterns.
5.  **Fleet Efficiency** --- occupancy, capacity, and operational
    efficiency measures.
6.  **Anomaly Detection** --- recorded anomaly categories and
    data-quality investigation flags.

The report uses slicers and interactive visuals so the displayed
measures respond to the selected report filters.

> 🖼️ Add the final screenshots of the six Power BI pages to the
> `screenshots/` folder. The image links below use the filenames in the
> proposed repository structure.

### Dashboard Preview

#### 1. Executive Overview
![Executive Overview](./screenshots/executive_overview.png)

#### 2. City Intelligence
![City Intelligence](./screenshots/city_intelligence.png)

#### 3. Service Reliability
![Service Reliability](./screenshots/service_reliability.png)

#### 4. Passenger Demand
![Passenger Demand](./screenshots/passenger_demand.png)

#### 5. Fleet Efficiency
![Fleet Efficiency](./screenshots/fleet_efficiency.png)

#### 6. Anomaly Detection
![Anomaly Detection](./screenshots/anomaly_detection.png)

## 💡 Findings from the Data-Quality Investigation

The cleaning notebook documents the following patterns:

-   **Boarding/passenger potential mismatch:** 46,333 records (9.27%)
    match the rule `boarding_count > 0` while `passenger_count == 0`.
    The rate differs across cities and route types in the notebook's
    group-level analysis.
-   **Status/delay potential mismatch:** 129,307 records (25.86%) match
    the notebook's investigation rule: `on_time` with a positive delay,
    or `minor_delay` / `major_delay` with zero delay.
-   **Cancellation consistency:** `cancellation_flag` matches the
    expected indicator derived from `service_status == "cancelled"` for
    all records checked.
-   **Occupancy consistency:** the occupancy audit reports a match
    between the stored occupancy rate and
    `passenger_count / vehicle_capacity` for all records with valid
    capacity under the notebook's comparison tolerance.

These are findings about the supplied synthetic dataset and the specific
checks defined in the notebook. The mismatch flags are not automatic
corrections or confirmed source-data errors.

## 📐 Fields & Analysis Areas

  -----------------------------------------------------------------------
  Area                                Fields examined
  ----------------------------------- -----------------------------------
  Trip and time                       `trip_id`, `timestamp`, `hour`,
                                      `day_name`

  Network                             `city`, `route_id`, `route_type`,
                                      `origin_station`, `dest_station`,
                                      `route_length_km`

  Passenger activity                  `passenger_count`,
                                      `boarding_count`, `alighting_count`

  Service and timing                  `service_status`,
                                      `scheduled_travel_min`,
                                      `actual_travel_min`,
                                      `delay_minutes`, `headway_min`

  Vehicle use                         `vehicle_capacity`,
                                      `occupancy_rate`

  Context                             `weather_condition`,
                                      `temperature_c`, `fare_type`

  Investigation flags                 `anomaly_type`, `anomaly_flag`,
                                      `boarding_passenger_mismatch`,
                                      `status_delay_mismatch`
  -----------------------------------------------------------------------

## ⚙️ How to Run the Analysis

### 1. Clone the repository

``` bash
git clone <your-repository-url>
cd Public-Transportation-Analytics
```

### 2. Install the required libraries

``` bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Add the dataset files

The notebooks expect the source CSV and the prepared CSV to be available
locally.

-   Place the source dataset at the path used by the data-cleaning
    notebook, or edit the `file_path` variable in that notebook.
-   After running the cleaning notebook, make sure the prepared CSV is
    saved at the location used by the EDA notebook, or update the EDA
    notebook's `pd.read_csv()` path.
-   For a portable GitHub setup, use paths relative to the project
    folder rather than the original local Windows paths.

### 4. Run the notebooks in order

1.  `Public_Transportation_Data_Cleaning.ipynb`
2.  `Public_Transportation_EDA.ipynb`

Run each notebook from top to bottom.

### 5. Open the Power BI report

Open `powerbi/Public_transport.pbix` using **Power BI Desktop**. If the
report asks for a data source location, update it to the location of
your prepared CSV.

## ⚠️ Limitations & Data Cautions

-   The dataset is synthetic and GTFS-inspired; it does not establish
    actual service conditions in London, Paris, Berlin, Tokyo, or New
    York.
-   The data-quality mismatch rules are investigation rules. They do not
    establish the cause of a discrepancy or identify which field should
    be corrected.
-   Passenger and service-status field definitions should be checked
    against the dataset documentation before making corrections or
    drawing operational conclusions.
-   The EDA notebook uses a 10,000-row sample for the passenger-count
    versus occupancy scatter plot.
-   The notebooks currently contain local Windows file paths. Update
    these paths when running the project on another machine.
-   The cleaned CSV was not supplied with the files used to prepare this
    README. Add the dataset separately if you plan to make it available
    in the repository, and check any dataset licence or sharing
    conditions first.

## 👨‍💻 Project Author

**Mohd Fuzail Salmani**\
Aspiring Business Intelligence Analyst \| Data Analytics \| Python • SQL
• Power BI

-   💼 LinkedIn: [Connect with
    me](https://www.linkedin.com/in/fuzailsalmani/)

## 🤝 Let's Connect & Discuss!

If you find this project useful:

-   ⭐ Star this repository.
-   💬 Open an issue or share suggestions for improving the analysis.
-   🔁 Share it with someone interested in Python, EDA, or Power BI.
-   🤝 Connect with me on LinkedIn to discuss data analytics and
    dashboard development.

**Which area would you investigate first: passenger demand, service
delays, fleet utilization, or the potential data-quality mismatches?**

------------------------------------------------------------------------

*Built with curiosity, data, and a focus on understanding transportation
data. 🚌* 
