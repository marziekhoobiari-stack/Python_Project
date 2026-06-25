# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

For this purpose the dataframe was filtered for top 3 most papular data roles. Then I got the top 5 skills for those roles. This highlights the skills that should be acquired for the targeted job title. 

View my notebook with detailed steps here: 
[2_Skills_Count.ipynb](Project\2_Skill_Count.ipynb)


### Visualization Data

```python 
fig, ax=plt.subplots(len(job_titles),1)
sns.set_theme(style='ticks')

for i , job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills',ax=ax[i], hue='skill_count', palette='dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].get_legend().remove()
    ax[i].set_xlim(0,78)

    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v +1 ,n, f'{v:.0f}%', va='center')

    if i != len(job_titles)-1:
        ax[i].set_xticks([])


fig.suptitle('Liklihood of Skills in US Job Postings', fontsize=15)
fig.tight_layout(h_pad=0.5)
plt.show()
```

### Results

![Visualization of Top Skills for Data Nerds](Project\Images\skill_demand_all_data_roles.png)


