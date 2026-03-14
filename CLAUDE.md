<challenge_overview>
# Predictive Grid Management for Heat Pump Networks

* [cite_start]**Goal:** Develop a high-precision predictive system that utilizes historical data from 2024 to forecast the total electrical load for the summer-autumn of 2025[cite: 8]. 
* [cite_start]**Task Nature:** This is an extrapolative challenge[cite: 11]. [cite_start]Participants must build models capable of projecting learned behaviors into a new year[cite: 9].
* [cite_start]**Timeframe:** Forecast May-October 2025 (6 months per device)[cite: 10].
* [cite_start]**Prediction Target:** For each device and forecast month, predict the average x2 over all 5-minute readings within that month[cite: 28].
</challenge_overview>

<data_specifications>
## Data Specifications
* [cite_start]**Frequency:** Data is recorded at 5-minute intervals[cite: 15].
* [cite_start]**Handling:** Due to the substantial volume of data, teams are expected to "slice" or subsample the dataset for efficient training and model development[cite: 16].
* [cite_start]**Synthesis:** The dataset consists of real-world telemetry; there is no requirement for generating additional synthetic data[cite: 17].
* [cite_start]**Download File:** `task 3 data oct24-oct25.tar.gz`[cite: 18].
</data_specifications>

<dataset_splits>
## Dataset Splits
| Subset | Period | Months | Notes |
| :--- | :--- | :--- | :--- |
| **Train** | Oct 2024-Apr 2025 | 7 months | [cite_start]Full feature set [cite: 20] |
| **Validation** | May 2025-Jun 2025 | 2 months | [cite_start]Partial feature set; x2 withheld [cite: 20] |
| **Test** | Jul 2025-Oct 2025 | 4 months | [cite_start]Partial feature set; x2 withheld [cite: 22] |
</dataset_splits>

<dataset_schema>
## Datasets Overview

### 1. Time-Series Telemetry (`data.csv`)
[cite_start]Time-series telemetry, one row per device per 5-minute interval[cite: 24].
* [cite_start]**Identifiers:** * `deviceld`: Unique identifier for each unit[cite: 21].
  * [cite_start]`Timedate`: UTC timestamp of the 5-minute reading[cite: 21].
* **Temperatures (all min-max normalised):**
  * [cite_start]`t1`: Outdoor ambient temperature[cite: 21].
  * [cite_start]`t2`: Indoor ambient temperature[cite: 21].
  * [cite_start]`t3`, `t4`: Temperature 1 & 2 on the source-side heat exchanger[cite: 21].
  * [cite_start]`t5`, `t6`: Temperature 1 & 2 on the receive-side heat exchanger[cite: 21].
  * [cite_start]`t7`: Domestic hot water storage tank temperature[cite: 21].
  * [cite_start]`t8`: Temperature 1 of the cooling circuit[cite: 21].
  * [cite_start]`t9`: Central heating buffer tank temperature[cite: 21].
  * [cite_start]`t10`, `t11`: Air temperature 1 & 2 at the source-side heat exchanger[cite: 21].
  * [cite_start]`t12`, `t13`: Temperature 3 & 4 on the receiver-side heat exchanger[cite: 21].
* **Operating Metrics:**
  * [cite_start]`x1`: Compressor/device operating frequency[cite: 21].
  * [cite_start]`x2`: Individual electrical grid load index (prediction target)[cite: 21].
  * [cite_start]`x3`: Type of heating curve configuration used by the device[cite: 21].
  * [cite_start]`deviceType`: Integer-encoded device category[cite: 21].

### 2. Static Metadata (`devices.csv`)
[cite_start]Static per-device metadata[cite: 25].
* [cite_start]`deviceld`: Unique identifier for each unit (join key)[cite: 26].
* [cite_start]`latitude`: Geographic latitude of the device installation site[cite: 26].
* [cite_start]`longitude`: Geographic longitude of the device installation site[cite: 26].
</dataset_schema>

<evaluation_metrics>
## Evaluation & Scoring
* [cite_start]**Metric:** Submissions are evaluated using MAE (Mean Absolute Error)[cite: 39]. [cite_start]Lower values indicate better predictions, and a score of 0 corresponds to a perfect prediction[cite: 41, 42].
* [cite_start]**Visible Leaderboard:** Validation only (May - Jun 2025)[cite: 44].
* [cite_start]**Final score:** Validation + Test (May - Oct 2025)[cite: 44].
* [cite_start]**Weights:** 2/6 valid, 4/6 test[cite: 44].
* [cite_start]**Requirement:** In order to be included in the final leaderboard, a reproducible code implementation for generating the submission should be provided, in a form of a link to public GitHub repository[cite: 45].
</evaluation_metrics>