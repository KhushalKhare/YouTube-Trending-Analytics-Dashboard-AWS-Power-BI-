

#  YouTube Global Trends Analytics Dashboard (AWS + PySpark + Power BI)

This project is an **end-to-end analytics solution** built using **AWS (Lambda, S3, PySpark)** and **Power BI**.
It transforms raw YouTube Trending data into a fully modeled BI dashboard with KPIs, trend analysis, category insights, and engagement metrics.

The goal was to build a pipeline that reflects real-world analytics work:
**ingestion → cleaning → transformation → modeling → visualization → insights.**

---

## 🚀 **Project Architecture**

```
YouTube Trending Dataset (JSON/CSV)
               │
               ▼
        AWS S3 (Raw Zone)
               │
               ▼
  AWS Lambda + PySpark (ETL & Cleaning)
     - Merge JSON & CSV files
     - Schema normalization
     - Publish time cleanup
     - Null handling & type conversions
               │
               ▼
        AWS S3 (Processed Zone)
               │
               ▼
        Power BI Analytics Layer
     - DAX Measures
     - KPI Engineering
     - Multi-page Dashboard
```

---

##  **AWS Lambda + PySpark ETL**

The ETL layer handles:

* Loading raw JSON/CSV files from S3
* Applying schema alignment
* Cleaning `publish_time` fields
* Normalizing nested JSON structures
* Removing invalid records
* Writing cleaned output back to S3

> Lambda code will be added to this repository soon.

---

##  **Power BI Dashboard**

The dashboard consists of **two pages**, designed for analytical clarity and storytelling.

---

### **1️ Page 1 Executive Overview**

**KPIs:**

* Total Likes
* Total Comments
* Video Count
* Channel Count
* Engagement Score
* Comment Intensity

**Visuals:**

* **Views Over Time** (Line Chart)
* **Top Categories by Views** (Bar Chart)
* **Engagement Score vs Views** (Scatter Plot)

---

### **2️ Page 2  Deep-Dive Analytics**

**Visuals:**

* **Top 10 Videos by Total Views**
* **Top 10 Videos by Engagement Score**
* **Detailed Matrix:**

  * region
  * publish_time_clean
  * likes/dislikes
  * views
  * comment_count
  * channel_title
  * engagement score

**Conditional formatting** applied for readability and insight detection.

---

##  **Key DAX Measures**

```DAX
Total_Views =
SUM('Table'[views])

Total_Comments =
SUM('Table'[comment_count])

Engagement Score =
DIVIDE(
    SUM('Table'[likes]) +
    SUM('Table'[dislikes]) +
    SUM('Table'[comment_count]),
    SUM('Table'[views])
)

Comment Intensity =
DIVIDE(
    SUM('Table'[comment_count]),
    SUM('Table'[views])
)

Video_count =
DISTINCTCOUNT('Table'[video_id])

Channel_count =
DISTINCTCOUNT('Table'[channel_title])
```

Additional measures include Like Ratio, Engagement per 1000 Views, and Avg Comments per Video.

---

##  **Skills Demonstrated**

### **AWS / Data Engineering**

* S3 storage architecture
* Lambda serverless ETL
* PySpark transformations
* JSON/CSV ingestion
* Schema normalization

### **Power BI / Analytics**

* Data modeling
* DAX (custom KPIs & metrics)
* Interactive dashboards
* KPI-driven storytelling
* Visual design standards

### **General Analytics Skills**

* KPI definition
* Performance analysis
* Engagement modeling
* Trend & category analysis

---



##  **Screenshots**

> Add PNGs of the dashboard here — Page 1 and Page 2.
> Page 1 Here's our logo (hover to see the title text):

Page 1: 
[Page 1](https://github.com/KhushalKhare/YouTube-Trending-Analytics-Dashboard-AWS-Power-BI-/blob/main/linkedin%20post%202.png")


Page 2:
[Page 2](https://github.com/KhushalKhare/YouTube-Trending-Analytics-Dashboard-AWS-Power-BI-/blob/main/linkedin%20post1.png")


