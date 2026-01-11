# Introduction
Welcome to my Data Analyst Portfolio Project! This repository contains a Python data analysis project focused on the analysis job market, uncovering top-paying roles, critical skills, and high-demand career pathways through data-driven exploration.

Check out my Python project here: [Python_Data_Project](https://github.com/LovelyLynn1993/Python_Data_Project)


# Questions
This project was motivated by a desire to better understand the data analyst job market through Python-driven analysis. The goal is to uncover which technical skills are both highly demanded and well compensated, using data to inform and optimize my job search strategy.

The data for this analysis is from [Luke Barousse’s Python Course](https://github.com/lukebarousse/Python_Data_Analytics_Course). This data includes details on job titles, salaries, locations, and required skills.

The questions I wanted to answer through my Python Data Project were:

1. What are the most demenaded skills for the top 3 most popular data roles?
2. How are in-demand skills trending for Data Analysis?
3. How well do jobs and skills pay for Data Analysts?
4. What is the most optimal skill to learn for Data Analysis, specifically high demand & high paying?


# Tools I Used
For this project, I utilized a variety of tools from the course in order to conduct my analysis:

- **Python (Core Language)**: *Used to automate data collection, cleaning, analysis, and visualization of job market data. Enables end-to-end analysis from raw job postings to actionable insights.*

- **Pandas Library**: *Cleaned and structured job posting data (titles, skills, salaries, locations).Performed filtering, grouping, and aggregation to identify trends in demand for data analyst skills.*

- **Matplot & Seaborn**: *Visualized trends such as:*

    1. *Most in-demand skills*
     2. *Job location distribution*
    3. *Salary ranges*
*This also create clear, presentation-ready charts and graphs.*

- **Jupyter Notebook**: Documented the analysis process with code, visuals, and explanations.Enabled exploratory data analysis and easy sharing of results.

- **Git & GitHub**: Version-controlled code and notebooks.Published the project as a portfolio piece demonstrating real-world analysis.

- **Visual Studio Code**: My go-to for executing my Python scripts.
t, followed by initial data cleaning taks to ensure data

# Data Preparation and Cleanup

This section outlines the steps taken to prepare the data for analyst, ensuring accuracy and usability.

### Import & Clean up Data

*Imported and cleaned data using Python by reading raw CSV and JSON files, standardizing column names, parsing dates, handling null values, and validating data quality with Pandas and NumPy.*

# The Analysis
This project leverages Python to analyze a real-world dataset of data science job postings with the goal of identifying top-paying roles and the most in-demand skills in the industry. Through exploratory data analysis, the project examines salary trends, job titles, and required technical skills to uncover patterns in the job market.

The insights generated from this analysis are intended to help job seekers make data-driven decisions when targeting high-value roles, prioritizing skill development, and navigating the data science job market more effectively. Below, I outline the strategic approach I took to address each question:

### 1. Top skills for leading Data Roles
This analysis determines the most in-demand skills for the three most common data roles by filtering job postings based on role frequency. For each of the top three roles, the top five required skills were extracted and ranked. 

The resulting query highlights the relationship between job title popularity and skill demand, providing role-specific insights into which technical skills should be prioritized when targeting each position.

View my notebook with detailed steps here: [1_Skill_Demand.ipynb](WIP\Project\1_Skill_Demand.ipynb)

### Visualize Data
```python
fig, ax = plt.sublots(len(job_titles), 1)

for i, job_titles in enermate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)[::-1]

sns.barplot(data=df_plot, x='skill_percent', y= 'job_skills', ax=ax[1], hue='skill_count', palette='blend:b,g')

plt.show()

```

### Results

![Likelihood of Skills Requesting in the US Job Postings'](Images\1_SkillsTrending.png)
*Bar graph visualizing the salary for the top 3 data roles and their top 5 skills associated with each.*

### Insights:

This analysis reveals that skill demand varies significantly across the most common data roles, underscoring the importance of aligning technical skill development with specific job targets. While some core skills appear consistently across roles, others are role-specific and reflect differing job responsibilities and expectations. 

By ranking the top skills for each of the three most popular positions, the results provide practical guidance for prioritizing learning efforts, enabling job seekers to focus on the technologies and tools that offer the greatest return for their desired role in the data field.

### 2. How are in-demand skills trending for Data Analysis?
To analyze skill trends for Data Analyst roles in 2023, job postings were filtered to include only Data Analyst positions and skills were grouped by the month each job was posted. This approach identified the top five skills per month, illustrating how demand for specific skills fluctuated throughout the year.

View my notebook with detailed steps here: [2_Skill_Trend.ipynb](WIP\Project\2_Skills_Trend.ipynb)

### Visualize Data
```python

from matplotlib.ticker import PercentFormatter

df_plot = df_DA_US_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, lengend='full', plaette='tab10')

plt.gca().yaxis.set-major_formatter(PercentFormatter(decimals=0))

plt.show()

```
### Results
![Trending Top Skills for Data Analyst in the US](Images\Trending_Skills.png) 
*Bar graph visualizing the trending top skills for data analysts in the US in 2023*

### Insights:

This analysis shows that demand for Data Analyst skills is not static but changes throughout the year, reflecting shifts in industry needs and hiring priorities. By tracking the top skills on a monthly basis, clear patterns emerge that highlight which technologies remain consistently valuable versus those that rise or fall in popularity over time. These trends provide actionable insight for job seekers, helping them time skill development strategically and focus on tools that demonstrate sustained or growing demand in the data analyst job market.

### 3. How well do jobs and skills pay for Data Analysts?

To identify the highest-paying roles and skills, job postings within the United States were filtered and analyzed using median salary values. Salary distributions were then examined for common data roles—such as Data Scientist, Data Engineer, and Data Analyst—to determine which positions offer the highest compensation.

View my notebook with detailed steps here: [3_Salary_Analysis](WIP\Project\3_Salary_Analysis.ipynb)

### Visualize Data
```python
sns.boxplot(data=df_US_top6, x='salary_year_avg', y='job_title_short', order=job_order)
sns.set_theme(style='ticks')
sns.despine()

plt.title('Salary Distributions of Data Jobs in the US')
plt.xlabel('Yearly Salary (USD)')
plt.ylabel('')
plt.xlim(0, 600000) 
ticks_x = plt.FuncFormatter(lambda y, pos: f'${int(y/1000)}K')
plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()

```


```python
fig, ax = plt.subplots(2, 1)

# Top 10 Highest Paid Skills for Data Analysts
sns.barplot(data=df_DA_top_pay, x='median', y=df_DA_top_pay.index, hue='median', ax=ax[0], palette='dark:b_r')
ax[0].legend().remove()
ax[0].set_title('Highest Paid Skills for Data Analysts in the US')
ax[0].set_ylabel('')
ax[0].set_xlabel('')
ax[0].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, _: f'${int(x/1000)}K'))

# Top 10 Most In-Demand Skills for Data Analysts')
sns.barplot(data=df_DA_skills, x='median', y=df_DA_skills.index, hue='median', ax=ax[1], palette='light:b')
ax[1].legend().remove()
ax[1].set_title('Most In-Demand Skills for Data Analysts in the US')
ax[1].set_ylabel('')
ax[1].set_xlabel('Median Salary (USD)')
ax[1].set_xlim(ax[0].get_xlim())  # Set the same x-axis limits as the first plot
ax[1].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, _: f'${int(x/1000)}K'))


plt.tight_layout()
plt.show()

```
### Results

![Salary distribution of Data jobs in the US](Images\Salary_Analysis.png)

![The Highest Paid & Most In-Demand Skills for data Analyst in the US](Images\High_Skill_Most_Demand.png) 


### Insights: 

This analysis highlights clear compensation differences across common data roles, demonstrating how job title significantly influences earning potential within the U.S. data job market. By comparing median salary distributions, it becomes evident which positions consistently command higher pay, reflecting variations in required expertise, responsibility, and market demand. These insights help job seekers better understand the financial trade-offs between roles and make more informed decisions when choosing career paths or prioritizing skill development.

### 4. What is the most optimal skill to learn for Data Analyst?
In order to identify the most optimal skill to learn for data analysis, is by examining both market demand and earning potential. Using Python, the percentage of job postings requiring each skill was calculated and then compared against median salary data to evaluate the trade-off between skill prevalence and compensation. 

By visualizing median salary versus percent skill demand, the analysis highlights skills that are not only widely requested but also associated with higher pay. This approach helps distinguish foundational tools from higher-value technologies and reveals which skills offer the strongest return on investment for aspiring data analysts, while also allowing for further investigation into the prevalence of specific technologies across the job market.

View my notebook with detailed steps here: [4_Optimal_Skills](WIP\Project\4_Optimal_Skills.ipynb)

### Visualize Data

```python
from adjustText import adjust_text
import matplotlib.pyplot as plt

plt.scatter (df_DA_skill_high_demand['skill_percent'], df_DA_skills_high_demand['median_salary'])
plt.show()

```
### Results

![Most optimal skills for Data Analyst in the US](Images\optimal_skills.png)


### Insights: 

This analysis shows that the most optimal skills for data analysts are those that balance strong market demand with higher salary potential, rather than excelling in only one dimension. Skills that appear frequently across job postings but also correlate with elevated median salaries represent the best return on learning investment, as they increase both employability and earning power. 

By breaking this relationship down with Python-driven analysis and visualization, the results help clarify which technologies are essential baseline requirements versus which ones can differentiate candidates in a competitive job market, enabling more strategic and data-driven skill development decisions.


# What I Learned

This project demonstrates how data-driven analysis can guide career planning in the data analyst field. By combining Python, Pandas, and Matplotlib with real-world job market data, I was able to identify which roles offer the highest salaries, which skills are most in-demand, and how skill demand changes over time. 

The insights not only highlight areas for personal skill development but also provide a roadmap for targeting high-value job opportunities. Overall, the project emphasizes how programming and data analysis skills can be applied to understand and navigate the job market strategically.

# Challenges 

This Project did have it's own challenges for sure, but I was able to learn new things and news ways:

- **Data Inconsistencies**: *Handling missing or inconsistent data entries did reqired careful consideration throughout the process.*
- **Complex Data Visualizaion**: *Overcoming designing effective visual representations of comples datasets.*
- **Balancing Breadth & Depth**: *Deciding how to deeply dive into each analysis while maintaining a broad overview that required constant balancing to ensure coverage without getting lost in the details.*

# Conclusion

This exporlation into the data analyst job market has been incredibly informative, highlighting critical skills and trends that shape this evolving field. 

The insights I obatined enhance my understanding and provide actionable guidance for anyone looking to advance their career, such as myself. As the market continues to change, ongoing analysis will be essential in order to stay ahead in data analytics. 

This project was a great way to explore data analytics and become a great foundation for future explorations and underscores the importance of continuous learning and adptaion in the data field.