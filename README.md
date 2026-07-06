# E-Commerce Fulfilment: IT Asset ETL Pipeline

## The Business Problem
A high-volume e-commerce fulfilment centre was experiencing critical shipping delays. Initial reports indicated hardware failures on the floor, but the existing IT asset database was corrupted with missing values, mismatched string formatting, and default date errors, making it impossible to identify the root cause of the delays.

## The Solution
I engineered an end-to-end ETL (Extract, Transform, Load) data pipeline to sanitise the corrupted logs and extract actionable operational intelligence.

* **Extract:** Ingested 5,000 rows of messy, real-world asset logs (simulated via Python/Numpy).
* **Transform:** Utilised `Pandas` to enforce business rules—cleansing string formatting (e.g., merging `Zone_A` and `Zone A`), handling null values, and correcting data types and impossible date anomalies. 
* **Load:** Pushed the sanitised dataset into a relational `SQLite` database.
* **Analyse:** Wrote optimised SQL queries using conditional aggregation (`CASE WHEN`) to isolate the exact operational bottlenecks.

## The Business Impact (Insights)
Through this pipeline, I identified two critical interventions for the Operations Director:
1. **The Maintenance Bottleneck:** Conveyor Sensors possess the highest failure rate per unit (2.07), requiring immediate preventative maintenance to stop line stoppages.
2. **The Volume Drain:** Handheld Scanners have an unacceptably high failure rate across a massive volume of units (1,671), indicating a vendor defect that is draining IT support hours. 
3. **The Hidden Bleed:** By fixing a string-formatting data anomaly, I revealed that "Zone A" was actually experiencing 544 down assets, making it the second most critical bottleneck in the facility, which the corrupted data was previously hiding.

## Tech Stack
* **Language:** Python 3
* **Data Manipulation:** Pandas, NumPy
* **Database & Querying:** SQLite, SQL