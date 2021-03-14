---
title: 'AGV打分'
date: 2020-07-17 16:03:58
tags:
- 实习
- DataAnalysis
---
# AGV打分

## AGV单日距离评分

### 仓库货架到工作站平均距离

* jjj_st: 105.9
* mc: 46.9
* CJLR: 82.66

理想距离: 各个货架到工作站的平均距离 &times; 2 &times; 货架数量

实际距离: tot_distance_with_c(containers) from agv_distance_by_hour

评分: 小于理想距离为满分， 大于理想距离按比例减分，最低0分

## AGV单日报错评分

### 每百千米报错

* jjj_st: 788, <23: 239
* mc: 1115, <23: 860
* CJLR: 241, <23: 211

理想报错: 历史平均报错次数

实际报错: count from agv_error_detail

评分: 小于理想报错为满分， 大于理想报错按比例减分，最低0分

## AGV单日工作时长评分

### 携带货架移动时长:

* jjj_st: 0.31-0.34 m/s
* mc: 0.13-0.15 m/s
* CJLR: 0.248-0.249 m/s

### 全部移动时长：历史时长拟合，和仓库规划严格相关

* jjj_st: 0.36-0.39 m/s
* mc: 0.15-0.16 m/s
* CJLR: 0.267-0.271 m/s

###  满载移动时长

* jjj_st: 0.474-0.504 m/s
* mc: 0.279-0.306 m/s
* CJLR: 0.438-0.440 m/s

实际时长: work_time+wait_time+load_time+release_time FROM agv_time_by_hour

评分: 总时长小于理想时长为满分,  大于理想报时长按比例减分，最低0分

## AGV充电时长评分

理想评分: 依赖携带货架运行距离&times;系数1&plus;不携带货架运行距离  &times;系数2

* 问题: 充电时间相对里程数没有增加

![image-20200708150322679](https://i.loli.net/2020/07/20/5UOw2fmgN6yHEn3.png)

* 问题2: 充电次数相对里程数也没有明显增加

![image-20200708150121650](https://i.loli.net/2020/07/20/HoLbciKGadDIjk7.png)

## 打分的综合情况

![AGV打分初步.png](https://i.loli.net/2020/07/21/ojGvYpUIrhcmCtB.png)
