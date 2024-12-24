# Data-analysis-project
A data analysis project which demonstrates the application of Python in analyzing and visualizing real-world data, covering techniques such as data cleaning, transformation, and exploratory data analysis using libraries like Pandas, Matplotlib, and Seaborn.

# Analysis
## 1. What are the most demanded skills for the top 3 most popular data jobs in the United States.
To find the most demanded skills for the top 3 most popular data roles. This query highlights the most popular job titles and their top skills, showing which skills to pay more attention to depending on the role that anyone is intrested in.
View my notebook with detailed code here: [2_skill_count.ipynb](https://github.com/tilakpatel07/Data-analysis-project/blob/main/2_skill_count.ipynb).

### Visualize Data
```python

fig, ax = plt.subplots(3, 1)
fig.set_size_inches(10, 6)

for i, job_title in enumerate(job_titles):
    df_job_title = df_plot_percentage[df_plot_percentage['job_title_short'] == job_title].head(5)
    # df_job_title.plot(kind='barh', x='job_skills', y='skill_percentage', ax=ax[i], legend=False)
    sns.set_theme(style='ticks')
    sns.barplot(data=df_job_title, x='skill_percentage', y='job_skills', ax=ax[i], hue='skill_percentage', palette='dark:b_r', legend=False)
    ax[i].set_title(f'{job_title}')
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].set_xlim(0, 100)
    if i != 2:
        ax[i].set_xticks([])

    for idx, val in enumerate(df_job_title['skill_percentage']):
        ax[i].text(val + 1, idx, f'{val:.0f}%', va='center')
    


fig.suptitle('Likehood of a skill being required for the top 3 job titles in the United States')
fig.tight_layout()
plt.show()

```

### Results 
