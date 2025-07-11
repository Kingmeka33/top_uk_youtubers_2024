# 📊 Excel to Power BI: YouTube Channel Insights Dashboard (UK - 2024)
![Image](https://github.com/user-attachments/assets/b8308c51-964f-457e-8d9d-b79b31b5119c)
A full-stack data portfolio project showcasing the transformation from Excel ➝ SQL ➝ Power BI to help a Marketing Team identify top-performing UK YouTubers for influencer campaigns.

---

## 📌 Table of Contents

- [🎯 Objective](#-objective)
- [📁 Data Source](#-data-source)
- [📈 Project Stages](#-project-stages)
- [🎨 Dashboard Design](#-dashboard-design)
- [🧰 Tools Used](#-tools-used)
- [⚙️ Development Process](#️-development-process)
- [🧪 Data Testing](#-data-testing)
- [📊 Power BI Dashboard](#-power-bi-dashboard)
- [🧮 DAX Measures](#-dax-measures)
- [🔍 Analysis & Findings](#-analysis--findings)
- [✅ Validation & ROI](#-validation--roi)
- [🔁 Recommendations & Actions](#-recommendations--actions)
- [📘 Conclusion](#-conclusion)
- [🙋‍♂️ Author](#-author)
- [📝 License](#-license)

---

## 🎯 Objective

**Pain Point:**  
The Head of Marketing wants to identify the top UK YouTubers in 2024 for collaboration opportunities in marketing campaigns.

**Goal:**  
Build a Power BI dashboard that provides insights on:
- Subscriber count
- Total views
- Total videos uploaded
- Engagement metrics

**User Story:**  
> As the Head of Marketing, I want to identify top-performing YouTube channels in the UK so I can choose the most impactful influencers to work with on upcoming campaigns.

---

## 📁 Data Source

**Origin:** [Kaggle Dataset (Excel)](https://kaggle.com)  
**Required Fields:**
- Channel name (extracted from a composite field)
- Total subscribers
- Total views
- Total videos uploaded

---

## 📈 Project Stages

1. Design
2. Development (ETL)
3. Testing
4. Analysis

---

## 🎨 Dashboard Design

### Questions Answered:
- Top 10 YouTubers by subscribers
- Top 3 by video uploads
- Top 3 by total views
- Channels with highest average views per video
- Channels with best views per subscriber ratio
- Channels with highest engagement rate

### Suggested Visuals:
- Table
- Treemap
- Scorecards
- Horizontal bar charts

---

## 🧰 Tools Used

| Tool        | Purpose                                |
|-------------|-----------------------------------------|
| Excel       | Initial data exploration                |
| SQL Server  | Data cleaning, testing, transformation  |
| Power BI    | Visualization                           |
| GitHub      | Version control, documentation          |
| Mokkup AI   | Dashboard wireframe/mockup              |

---

## ⚙️ Development Process

### Pseudocode Overview:
```text
1. Import Excel data
2. Explore in Excel
3. Load to SQL Server
4. Clean and transform with SQL
5. Validate data
6. Build Power BI dashboard
7. Publish and document on GitHub
```

### SQL View Creation:
```sql
CREATE VIEW view_uk_youtubers_2024 AS
SELECT
    CAST(SUBSTRING(NOMBRE, 1, CHARINDEX('@', NOMBRE) - 1) AS VARCHAR(100)) AS channel_name,
    total_subscribers,
    total_views,
    total_videos
FROM top_uk_youtubers_2024;
```

---

## 🧪 Data Testing

### Row Count Check
```sql
SELECT COUNT(*) FROM view_uk_youtubers_2024;
```

### Column Count Check
```sql
SELECT COUNT(*) 
FROM INFORMATION_SCHEMA.COLUMNS 
WHERE TABLE_NAME = 'view_uk_youtubers_2024';
```

### Data Type Check
```sql
SELECT COLUMN_NAME, DATA_TYPE 
FROM INFORMATION_SCHEMA.COLUMNS 
WHERE TABLE_NAME = 'view_uk_youtubers_2024';
```

### Duplicate Check
```sql
SELECT channel_name, COUNT(*) 
FROM view_uk_youtubers_2024 
GROUP BY channel_name 
HAVING COUNT(*) > 1;
```

---

## 📊 Power BI Dashboard

![Dashboard GIF or Screenshot](dashboard-preview.gif)  
> Shows top UK YouTubers by subscribers, views, uploads, and engagement rates.

---

## 🧮 DAX Measures

```dax
-- Total Subscribers (M)
Total Subscribers (M) = DIVIDE(SUM(view_uk_youtubers_2024[total_subscribers]), 1000000)

-- Total Views (B)
Total Views (B) = ROUND(SUM(view_uk_youtubers_2024[total_views]) / 1000000000, 2)

-- Total Videos
Total Videos = SUM(view_uk_youtubers_2024[total_videos])

-- Average Views per Video (M)
Average Views per Video (M) = 
    DIVIDE(SUM(view_uk_youtubers_2024[total_views]), SUM(view_uk_youtubers_2024[total_videos])) / 1000000

-- Subscriber Engagement Rate
Subscriber Engagement Rate = 
    DIVIDE(SUM(view_uk_youtubers_2024[total_subscribers]), SUM(view_uk_youtubers_2024[total_videos]))

-- Views per Subscriber
Views Per Subscriber = 
    DIVIDE(SUM(view_uk_youtubers_2024[total_views]), SUM(view_uk_youtubers_2024[total_subscribers]))
```

---

## 🔍 Analysis & Findings

### Top YouTubers by Subscribers
| Rank | Channel Name        | Subs (M) |
|------|----------------------|----------|
| 1    | NoCopyrightSounds   | 33.6     |
| 2    | DanTDM              | 28.6     |
| 3    | Dan Rhodes          | 26.5     |

### Top by Videos Uploaded
- GRM Daily
- Manchester City
- Yogscast

### Most Views
- DanTDM
- Dan Rhodes
- Mister Max

### Highest Avg Views Per Video
- Mark Ronson (32.27M)
- Jessie J (5.97M)
- Dua Lipa (5.76M)

### Views per Subscriber
- GRM Daily (1185.79)
- Nickelodeon (1061.04)
- Disney Junior UK (1031.97)

---

## ✅ Validation & ROI

### Example ROI (Product Placement):
**Dan Rhodes**
- Avg Views: 11.15M
- 2% Conversion → 223K units
- Revenue: $1,115,000
- Cost: $50,000
- **Net Profit:** $1,065,000

**Mister Max**
- Revenue: $1,406,000
- Cost: $130,000
- **Net Profit:** $1,276,000

---

## 🔁 Recommendations & Actions

### Recommended Collaborations:
1. **Dan Rhodes** – Best ROI
2. **DanTDM** – Strong reach & brand alignment
3. **NoCopyrightSounds** – High profitability

### Action Plan:
- Reach out to Dan Rhodes team first
- Monitor performance against KPIs
- Scale collaboration based on campaign success

---

## 📘 Conclusion

This project demonstrates a practical use-case of transforming messy Excel data into a validated, ROI-driven Power BI dashboard using SQL and DAX. It enables strategic influencer decisions backed by reliable metrics.
