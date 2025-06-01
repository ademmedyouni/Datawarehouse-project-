# IT Jobs Comparison Dashboard: ETL Process and Visualization with Power BI

## Project Overview
This project aims to develop a Business Intelligence (BI) dashboard for comparing IT jobs globally and specifically in Tunisia. The process involves data extraction, transformation, loading (ETL), and visualization using Power BI. The goal is to provide insights into job trends, required skills, and salary comparisons to aid decision-making for professionals, students, and recruiters.

## Key Features
- **Data Collection**: Extracted IT job data from global sources (Kaggle) and Tunisian job portals (Keejob, Tantijobs) using web scraping.
- **ETL Process**: Utilized SSIS and SSMS to clean, transform, and load data into a dimensional data warehouse.
- **Power BI Dashboard**: Interactive visualizations to analyze job trends, salaries, and skills across regions.

## Technologies Used
- **Data Extraction**: Python (BeautifulSoup, Pandas), Web Scraping
- **ETL**: SQL Server Integration Services (SSIS), SQL Server Management Studio (SSMS)
- **Data Warehouse**: Dimensional modeling (Fact and Dimension tables)
- **Visualization**: Power BI

## Project Structure
1. **Data Extraction**:
   - Global IT jobs dataset from Kaggle.
   - Tunisian IT jobs scraped from Keejob and Tantijobs.
   - Python scripts for scraping and preprocessing.

2. **Staging Area**:
   - Temporary storage for raw data before transformation.
   - SQL queries for initial cleaning (handling null values, currency conversion).

3. **Data Transformation**:
   - SQL scripts to standardize salaries (e.g., converting TND to USD).
   - Removal of incomplete records (e.g., missing job titles or skills).

4. **Data Warehouse**:
   - Dimensional tables: `dim_time`, `dim_region`, `dim_country`, etc.
   - Fact table: `fact_salary` with keys linking to dimension tables.

5. **Power BI Dashboard**:
   - Interactive visuals for comparing salaries, experience levels, and skills.
   - Filters for regions, years, and job types.

## Code Examples
### Web Scraping (Python)
```python
import requests
from bs4 import BeautifulSoup
import pandas as pd

base_url = "https://www.keejob.com/offres-emploi/?professions_parent=24"
def extract_jobs_from_page(url):
    response = requests.get(url)
    soup = BeautifulSoup(response.content, 'html.parser')
    job_listings = []
    # Extract job details (title, company, location, etc.)
    return job_listings
```

### SQL Transformation
```sql
-- Fill null salaries with minimum salary
UPDATE dbo.stagingarea
SET salary = (SELECT MIN(salary) FROM dbo.stagingarea WHERE salary IS NOT NULL)
WHERE salary IS NULL;
```

## How to Use
1. **Run ETL Pipeline**:
   - Execute SSIS packages to extract, transform, and load data into the warehouse.
2. **Open Power BI**:
   - Connect to the data warehouse and refresh the dashboard for updated insights.

## Contributors
- Adem Medyouni
- Nourhene Ayari

---

For detailed steps or troubleshooting, refer to the project documentation or contact the contributors.
``` 
