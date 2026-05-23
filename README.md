# Data_Visualiazation
The purpose of this repository is to analyze and gain insights from a dataset from Kaggle for a project for our college.

🇨🇦 Canadian Data & Analytics Job Market Dataset
A cleaned dataset of 1,796 data and analytics job postings from across Canada, covering roles from entry-level analysts to senior business intelligence specialists. Built for exploratory data analysis, salary benchmarking, skills research, and job market visualization.

📁 Dataset Overview
AttributeDetailsFileCleaned_Dataset.csvRows1,796 job postingsColumns13Missing ValuesNone

🗂️ Column Descriptions
ColumnTypeDescriptionJob TitleStringBroad role category (e.g., Systems and Data Analysts, Business and Marketing Analysts)Job InfoStringFull job posting title as listed by the employerPositionStringStandardized position label (e.g., Analyst, Data Engineer, Business Analyst)EmployerStringHiring organization nameCityStringCity where the role is located (or Remote)ProvinceStringCanadian province abbreviation (e.g., ON, BC, QC); Undef where unspecifiedSkillStringComma-separated list of technical skills mentioned in the postingSeniorityStringExperience level: ANY, Junior, Mid, or SeniorWork TypeStringWork arrangement: In-Person, Remote, or HybridIndustry TypeStringSector of the hiring organization (e.g., Technology, Healthcare, Finance)Min_SalaryFloatMinimum annual salary (CAD)Max_SalaryFloatMaximum annual salary (CAD)Avg_SalaryFloatAverage of min and max salary (CAD)

📊 Key Statistics
Salary (CAD)
MetricMin SalaryMax SalaryAvg SalaryMean$68,664$88,205$78,435Median$68,000$87,000$77,750Std Dev$18,793$20,038$18,027Range$30,241 – $137,280$57,200 – $180,000$43,720 – $158,640
Top Positions
PositionCountAnalyst780Business Analyst327Data Analyst229System Analyst182Data Engineer41
Geographic Distribution
ProvincePostingsOntario (ON)949British Columbia (BC)243Alberta (AB)192Quebec (QC)176Others232
Work Type

In-Person: 91.1%
Remote: 7.8%
Hybrid: 1.1%

Seniority Level

Open / Any: 75.7%
Senior: 20.5%
Mid-level: 2.0%
Junior: 1.8%


💡 Potential Use Cases

Salary benchmarking — Compare pay across provinces, industries, and seniority levels
Skills analysis — Identify the most in-demand technical skills (Python, SQL, Power BI, etc.)
Job market trends — Explore remote vs. in-person demand across Canada
Industry comparison — Contrast hiring activity in Technology, Healthcare, Finance, and more
Career path research — Map position types to salary ranges and required skills


🚀 Quick Start
pythonimport pandas as pd

df = pd.read_csv("Cleaned_Dataset.csv")
print(df.shape)        # (1796, 13)
print(df.head())
print(df.describe())
Parse the Skill column into lists for skills frequency analysis:
pythonfrom collections import Counter

all_skills = df["Skill"].dropna().str.split(", ").explode()
top_skills = Counter(all_skills).most_common(10)
print(top_skills)

📌 Notes

Province is marked Undef for postings that did not specify a location.
Avg_Salary is computed as (Min_Salary + Max_Salary) / 2.
Seniority ANY indicates the posting did not specify an experience level requirement.
Skills are extracted directly from posting text and may contain slight variations (e.g., Power BI vs Power Bi).
