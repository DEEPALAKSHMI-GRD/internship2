 Big Data Analysis with Dask
 
 Main Libraries Used:
dask.dataframe – for scalable big data processing

Dataset:
Reads data from:yellow_tripdata_2023-01.parquet

Main Steps in the Notebook:
Load Data

import dask.dataframe as dd
df = dd.read_parquet("yellow_tripdata_2023-01.parquet")

Data Cleaning

Drops rows with missing values in:

tpep_pickup_datetime

tpep_dropoff_datetime

trip_distance

fare_amount

Removes rows where trip_distance or fare_amount ≤ 0.


 Feature Extraction

Extracts pickup hour from tpep_pickup_datetime.

Aggregation

Trip count per hour

Average fare per hour

Average distance per hour


trip_count = df.groupby('hour').size().compute()
avg_fare = df.groupby('hour').fare_amount.mean().compute()
avg_distance = df.groupby('hour').trip_distance.mean().compute()

