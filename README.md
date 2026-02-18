# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular roles. O filteres out those positions by which ones were most popular, and got the top 5 skills for these top 3 roles. This query shows which skills I should be learning based on the role I would like to get in my future.

view my notebook with detailed steps here: [2_Skills_Count.ipynb](C:\Users\frant\Phyton_Data_Course\3_Project\2_Skills_Count.ipynb)

### Visualize Data

```python

fig,ax=plt.subplots(len(job_titles),1)

for i,job_title in enumerate (job_titles):
    df_plot=df_skills_count[df_skills_count['job_title_short']==job_title].head(5)
    df_plot.plot(kind='barh',x='job_skills',y='skills_count',ax=ax[i],legend=False)
    ax[i].set_title(f'Top Skills for {job_title}')
plt.tight_layout()
plt.show()
```

### Results

![Visualization of Top skills](Images\Skill_demand_percent.png)

### Insights
- SQL emerges as the most valuable skill across the top three data-related roles, remaining consistently in demand regardless of the level of technical complexity required.

- Python is the most predominantly demanded skill for Data Scientists, appearing in 72% of job postings, followed closely by Data Engineers at 65%.

- Data Engineers are expected to possess more advanced technical expertise, including cloud and big-data technologies such as AWS, Azure, and Spark. In contrast, Data Scientists and Data Analysts rely more heavily on data management and visualization tools, with strong demand for skills such as Tableau and Excel.-Python is the most predomintaly demanded skill for Data Scientists with a 72% and then Data Engineers with a 65%

## 2. How are in-demand skills trending for Data Analysts? 

### Visualize Data

```python

df_plot=df_DA_US_percent.iloc[:,:5]

sns.lineplot(data=df_plot,dashes=False, palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

plt.title('Trending Top Skills for Data Analysts in the US')
plt.ylabel('Likelihhod in Job Posting')
plt.xlabel('2023')
plt.legend().remove()

from matplotlib.ticker import PercentFormatter
ax= plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

for i in range(5):
    plt.text(11.2, df_plot.iloc[-1,i], df_plot.columns[i])

```
###  Results

![Visualization of Skill Trends](Images\Skill_trend.png)

### Insights 

- SQL continues to be the most prominent skill throughout the year, showing a higher probability of being mentioned in job postings, especially between April and June.

- Excel ranks second, surpassing Python and Tableau. It shows steady demand during the first months of the year, followed by a decline between August and October, and a rebound towards the end of the year.

- Python and Tableau exhibit similar behavior, with fluctuations throughout the year. Python reaches its peak demand in December, while Tableau sees its highest demand in August.

- Finally, Power BI records the lowest values, indicating relatively low demand throughout the year compared to the other skills analyzed.

## 3. How well do jobs and skills pay for Data Analysts?

### Salary Analysis(Jobs)
### Visualize Data

```python
sns.boxplot(data=df_US_top6, x='salary_year_avg', y='job_title_short', order=job_order)
sns.set_theme(style='ticks')

plt.title('Salary Distributions in the United States')
plt.xlabel('Yearly Salary (USD)')
plt.ylabel('')
plt.xlim(0, 600000) 
ticks_x = plt.FuncFormatter(lambda y, pos: f'${int(y/1000)}K')
plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()
```

### Results

![Visualization of  Jobs Median Salary](Images\Job_Salary.png)

#### Insights

- The median Salaries tend to increase with seniority suggesting that experience for this specific career path is highly valuable.

- Data Scientists and Data Engineer roles show a greater amount of outliers suggesting that having better skills will lead to higher paying jobs, while Data Analyst roles show more cosistency with not that many outliers.

- Data Analyst roles have a lower median salary overall compared to Data Scientist and Data Engineer roles which might required more technical skills and sophistacated studies or experience. 

## 4. Salary Analysis(Skills)
### Visualize Data

```python
fig, ax = plt.subplots(2, 1)  

sns.set_theme(style='ticks')

# Top 10 Highest Paid Skills for Data Analysts
sns.barplot(data=df_DA_top_pay, x='median', y=df_DA_top_pay.index, hue='median', ax=ax[0], palette='dark:b_r')
ax[0].legend().remove()
# original code:
# df_DA_top_pay[::-1].plot(kind='barh', y='median', ax=ax[0], legend=False) 
ax[0].set_title('Top 10 Highest Paid Skills for Data Analysts')
ax[0].set_ylabel('')
ax[0].set_xlabel('')
ax[0].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, _: f'${int(x/1000)}K'))


# Top 10 Most In-Demand Skills for Data Analystsr')
sns.barplot(data=df_DA_skills, x='median', y=df_DA_skills.index, hue='median', ax=ax[1], palette='light:b')
ax[1].legend().remove()
# original code:
# df_DA_skills[::-1].plot(kind='barh', y='median', ax=ax[1], legend=False)
ax[1].set_title('Top 10 Most In-Demand Skills for Data Analysts')
ax[1].set_ylabel('')
ax[1].set_xlabel('Median Salary (USD)')
ax[1].set_xlim(ax[0].get_xlim())  # Set the same x-axis limits as the first plot
ax[1].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, _: f'${int(x/1000)}K'))

plt.tight_layout()
plt.show()
```

### Results

![Visualization of  Jobs Median Salary](Images\Skills_Salary.png)

#### Insights

- Bla bla bla
- Bla bla bla
- Bla bla bla

## 5. Optimal skills for Data Analysts in the US

## 1. What are the better paid and most popular skills among Data Analyst in the US?


### Visualize Data

```python

fig, ax = plt.subplots(figsize=(10, 6))

# Scatter plot
ax.scatter(
    df_DA_skills_high_demand["skill_percent"],
    df_DA_skills_high_demand["median_salary"]
)

# Prepare texts for adjustText
texts = []
for i, txt in enumerate(df_DA_skills_high_demand.index):
    texts.append(
        ax.text(
            df_DA_skills_high_demand["skill_percent"].iloc[i],
            df_DA_skills_high_demand["median_salary"].iloc[i],
            str(txt)
        )
    )

```
### Results

![Visualization of Optimal skills](Images\Optimal_Skills.png)

### Insights
-
-
-
