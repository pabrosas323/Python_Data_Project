# The Analysis

## 1. What are the most demanded skills for the most popular data roles?

To find the most demanded skills for the top 3 most popular data roles in 2023. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top roles. These visualizations highlight the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm looking for. 

View my notebook with detailed steps here: [2_Skills_Count.ipynb](2_Skills_Count.ipynb)

### Visualize Data


```python
    for i, job_title in enumerate(job_titles): #looping through each job title
        df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5) #filtering for only that job title
    
        sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r', legend=False)
    plt.show()
```
### Results

![Visualization of Top Skills for Data Roles](Images/skills_count.png)

### Insights

- Python is a highly versatile skill that is prominent across all job roles, but mostly for Data Engineers (65%) and Scientists (72%)
- SQL is the most highly requested skill for Data Analysts (51%) and Engineers (68%)
- Data Engineers require more specialized skills (AWS, Azure, Spark) compared to the other 2 roles. Data Scientists seem to lean more towards general data management and analysis tools (Tableau, SQL).

## 2. How Are In-Demand Skills Trending for Data Analysts?

For this visualization, I again filtered for Data Analyst roles in the United States, and created a pivot table with the months as the index, and the skills as the columns. I then chose the top 5 skills, and created a lineplot showing how these skills were trending during 2023. 

View my notebook with detailed steps here: [3_Skills_Trend.ipynb](3_Skills_Trend.ipynb)
### Visualize Data

```python
df_top_5 = df_percent.iloc[:,:5] #choosing top 5 skills
fig, ax = plt.subplots()
sns.lineplot(data=df_top_5, dashes=False, palette='tab10')
ax.yaxis.set_major_formatter(plt.FuncFormatter(lambda y, pos: f'{y:.0f}%'))
plt.show()
```

### Results

![Visualization of Trending Skills for US Data Analysts](Images/trending_skills.png)

### Insights

- SQL remains as the most popular skills, but interestingly, it has shown a gradual decline through the year of 2023.
- Excel remains the second most popular skill, mostly staying steady until August, where it declines by almost 10% through November.
- Python and Tableau show very similar behavior and likelihood throughout the year, except in August, where Python has a sharp but short-lived increase.