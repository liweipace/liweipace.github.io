---
title: 'AGV在不同仓库间横向对比分析'
date: 2020-07-21 21:53:58
tags:
- 实习
- DataAnalysis
---
# AGV分析

## AGV历史平均速度

* 这里简单筛选AGV两次动作之间小于10s，这两个动作之间的时间和距离算作有效时间和有效距离
* 携带货架计为heavy_time
* 不携带货架计为easy_time
* warehouse_size依赖每个货架到工作站的平均距离---拍脑袋想出来的自定义指标

| warehouse_id | easy_velocity | heavy_velocity | warehouse_size |
| ------------ | ------------- | -------------- | -------------- |
| jjj_st       | 0.74          | 0.51           | 105.9          |
| LS-CP-01     | 0.65          | 0.4            | 82.66          |
| 809          | 0.52          | 0.3            | 46.9           |
| abs_sq       | 0.56          | 0.4            | 73.4           |
| BXYK3C       | 0.2           | 0.04           | 31.7           |
| hc_zj        | 0.48          | 0.37           | 53.1           |
| eos_ks       | 0.2           | 0.16           | 43.3           |
| sabs         | 0.24          | 0.14           | None           |

* 当仓库设计的时候，机器人实际运行速度可以通过历史仓库数据给出一个区间（精确值不可能给到，毕竟仓库数量还不够多）

![image-20200716140323752](https://i.loli.net/2020/07/20/9b6I1KczaHeDYlJ.png)

## AGV LifeTime Analysis

* 2020-05-07 08:30:00 - 17:00:00 
* CJLR随机的5台机器全时段全状态分布

![微信图片_20200721092343](https://i.loli.net/2020/07/21/mz1uUsTINDrRLF5.png)

## AGV工作时长统计，按小时

![image-20200716152111751](https://i.loli.net/2020/07/20/j4DlcbEaUJP18k3.png)

## 历史报错次数按位置分布(以CJLR为例)

* 各类型错误可以在网页通过Tab切换

![image-20200716130808644](https://i.loli.net/2020/07/20/HW2L3wJ9Uzg6vfn.png)

## 全仓每百公里报错横向对比雷达

* 在网页交互中可以自由选择查看不同的仓库
* 由于pyecharts的雷达图bug，legend无法和图线颜色对应
* 最佳仓库是cjlr和jjj，指标较小
* 最差仓库是809和hc，指标偏大，禾川存在运行距离过短的问题，可能造成取平均效果不佳

![AGV报错在仓库横向比较](https://i.loli.net/2020/07/20/rloyN5VXpc6Jf4C.png)

![AGV报错在仓库横向比较 (1)](https://i.loli.net/2020/07/20/3gYaecFJmR6EUPw.png)

![AGV报错在仓库横向比较](https://i.loli.net/2020/07/20/wLDHm7gJCeqlzyf.png)
