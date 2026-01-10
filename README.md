# Introduction
Welcome to my Data Analyst Portfolio Project! This repository contains a Python data analysis project focused on the analysis job market, uncovering top-paying roles, critical skills, and high-demand career pathways through data-driven exploration.

Check out my Python project here: [Python_Data_Project]


# Background
This project was motivated by a desire to better understand the data analyst job market through Python-driven analysis. The goal is to uncover which technical skills are both highly demanded and well compensated, using data to inform and optimize my job search strategy.

The data for this analysis is from [Luke Barousse’s Python Course](). This data includes details on job titles, salaries, locations, and required skills.

The questions I wanted to answer through my Python Data Project were:

1. What are the most demenaded skills for the top 3 most popular data roles?
2. How are in-demand skills trending for Data Analysis?
3. How well do jobs and skills pay for Data Analysts?
4. What is the most optimal skill to learn for Data Analysis, specifically high demand & high paying?


# Tools I Used
For this project, I utilized a variety of tools from the course in order to conduct my analysis:

Visual Studio Code: Visual Studio Code served as the primary development environment for this project, enabling efficient Python development and seamless execution of database queries.



# The Analysis
In this project, each query was designed to uncover key insights into the data analyst job market. Below, I outline the strategic approach I took to address each question:

### 1. Top skills for leading data roles

### Visualize Data

### Results
View my notebook with detailed steps here: [2_Skill_Demand.ipynb](WIP\2_Skill_Demand.ipynb)

### Insights:

### 2. How are in-demand skills trending for Data Analysis?

### Visualize Data

### Results
[Trending Top Skills for Data Analyst in the US]() 

### Insights:


### 3. How well do jobs and skills pay for Data Analysts?

### Salary Analysis for Data Nerds

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
![Salary distribution of Data jobs in the US](Images\Salary_Analysis.png)


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

![The Highest Paid & Most In-Demand Skills for data Analyst in the US](Images\High_Skill_Most_Demand.png) 


### Insights: 

### 3. How well do jobs and skills pay for Data Analysts?

### Salary Analysis for Data Nerds

### Visualize Data

### Results




### Insights: 
# Conclusion