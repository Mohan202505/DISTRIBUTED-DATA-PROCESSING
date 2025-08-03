# DISTRIBUTED-DATA-PROCESSING
🚲 Bike Trips Data Preprocessing with PySpark
📌 Project Overview
This project involves data preprocessing using Apache Spark on a bike-sharing dataset. The dataset includes information such as trip duration, start and end times, stations, user types, gender, and birth year. The goal is to clean, filter, and aggregate the data to derive useful insights.

📂 Dataset Schema
php
Copy
Edit
-- trip_id: integer (nullable = true)
-- starttime: string (nullable = true)
-- stoptime: string (nullable = true)
-- bikeid: integer (nullable = true)
-- tripduration: integer (nullable = true)
-- from_station_id: integer (nullable = true)
-- from_station_name: string (nullable = true)
-- to_station_id: integer (nullable = true)
-- to_station_name: string (nullable = true)
-- usertype: string (nullable = true)
-- gender: string (nullable = true)
-- birthyear: integer (nullable = true)
⚙️ Technologies Used
Apache Spark (PySpark)

Python 3.x

Jupyter Notebook / VSCode / Databricks (any environment of your choice)

📦 Installation & Setup
Install Java (JDK 8 or higher)

Install Apache Spark

Install findspark (optional)

bash
Copy
Edit
pip install pyspark
pip install findspark
Set environment variables for Java and Spark if needed.

📑 Tasks Performed
✅ Data Loading
python
Copy
Edit
df = spark.read.csv("path/to/your/bike_data.csv", header=True, inferSchema=True)
✅ Data Filtering
Trips longer than 30 minutes:

python
Copy
Edit
df.filter(col("tripduration") > 1800)
Male users only:

python
Copy
Edit
df.filter(col("gender") == "Male")
Users born after 1990:

python
Copy
Edit
df.filter(col("birthyear") > 1990)
Subscribers only:

python
Copy
Edit
df.filter(col("usertype") == "Subscriber")
✅ Data Aggregation
Average trip duration by gender:

python
Copy
Edit
df.groupBy("gender").agg(avg("tripduration").alias("avg_trip_duration"))
Count of trips by user type:

python
Copy
Edit
df.groupBy("usertype").agg(count("*").alias("trip_count"))
Max and Min trip durations:

python
Copy
Edit
df.agg(
    max("tripduration").alias("max_duration"),
    min("tripduration").alias("min_duration")
)
Trips from each station:

python
Copy
Edit
df.groupBy("from_station_name").count().orderBy("count", ascending=False)
Average trip duration per birth year:

python
Copy
Edit
df.groupBy("birthyear").agg(avg("tripduration").alias("avg_trip_duration"))
📁 Output Files
Processed outputs can be saved to CSV:

python
Copy
Edit
result.write.csv("output/folder_name.csv", header=True)
