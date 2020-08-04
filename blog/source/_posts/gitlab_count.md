---
title: '实习代码量统计'
date: 2020-07-22 11:10:58
tags:
- WorkReport
- gitlab
- python-gitlab
---
# 实习代码量统计
<!--more-->
## Gitlab主页统计

![04c7ec9c30130a880828895542491ce](https://i.loli.net/2020/07/22/u4pGtAY9zB2bOHv.png)

## Python-gitlab包统计结果

```python
import gitlab
import pandas as pd
url = 'http://192.168.188.25*:**/' # 手动隐藏端口名
private_token = 'JctqLQ4D1W-5oYqY6y**' # 手动隐藏token
gl = gitlab.Gitlab(url, private_token)
start_time = '2020-01-01T00:00:00Z'
end_time = '2020-07-22T00:00:00Z'
projects = gl.projects.list(all=True) # 获得所有项目
stats = []
for project in projects: # 遍历每一个项目
    branches = project.branches.list() # 获得所有分支
    for branch in branches: # 遍历每一个分支
        commits = project.commits.list(
            all=True,query_parameters={
            	'since': start_time,
            	'until':end_time, 
            	'ref_name': branch.name
            }
        ) # 根据时间、分支名遍历该分支下面所有的提交记录
        for commit in commits: # 然后再遍历每个提交记录，查询每个提交记录的人和量
            com = project.commits.get(commit.id)
            #print(com.committer_email)
            stats.append([
                com.committer_email,
                com.stats['additions'],
                com.stats['deletions'],
                com.stats['total']
            ])
commit_history = pd.DataFrame(stats, columns=['email', 'additions', 'deletions', 'total'])
commit_history = commit_history.groupby('email').agg(
    {
        'additions':['count', 'sum'],
        'deletions':'sum', 
        'total':'sum'
    }
)
commit_history.columns=['count', 'additions', 'deletions', 'total']
commit_history = commit_history.sort_values('count', ascending=False)
print(commit_history)
```

* 打印结果

| email                                     | count | additions | deletions | total   |
| ----------------------------------------- | ----- | --------- | --------- | ------- |
| liwei@maluinnovation.com                  | 311   | 2394779   | 621253    | 3016032 |
| zhang**@maluinnovation.com # 隐藏同事姓名 | 55    | 96359     | 45094     | 141453  |
| liqi**@maluinnovation.com# 隐藏同事姓名   | 27    | 24930     | 7804      | 32734   |
| dingch**@maluinnovation.com# 隐藏同事姓名 | 2     | 173       | 6         | 179     |
