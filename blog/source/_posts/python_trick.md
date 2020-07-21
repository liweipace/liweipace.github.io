---
title: 'Python优化的一些注意事项'
date: 2020-07-20 15:53:58
tags:
- 实习
- DataAnalysis
- Python
---
# Python优化

## 取SQL速度

由于数据库维护，全量更新等等原因，所以优先查看数据库索引是否健全，其次优化语句

### 索引注意事项

* 推荐选择: <, <=, =, >, >=, like(aaa%), between
* 不要在列上做运算, 例如substr(time), YEAR(time)
* 不适用NOT, IN, <>操作(因为IN是一个OR操作)
* 不适用like(%aaa%)

## Never pandas append

```python
start = time.time()
sample = []
for i in range(10000):
    sample.append([random.random(),random.random()])
df = pd.DataFrame(sample, columns=['a','b'])
print(df.shape)
end = time.time()
print('Running time: %s Seconds'%(end-start))
```

```
(10000, 2)
Running time: 0.022986650466918945 Seconds
```

```python
start = time.time()
df = pd.DataFrame([], columns=['a','b'])
for i in range(10000):
    new_row = pd.Series({'a':random.random(),'b':random.random()})
    df = df.append(new_row, ignore_index=True)
print(df.shape)
end = time.time()
print('Running time: %s Seconds'%(end-start))
```

```
(10000, 2)
Running time: 33.58438324928284 Seconds
```

## if-elif-elif-else

循环中将概率较高的判断放在靠前的语句中

## 字典

字典查询复杂度是O(1)，list查询复杂度是O(n)，查询类型的可以把list先转换成字典

## OPTIONAL：循环外能计算的部分先计算

```python
k = len(a)
for i in range(k):
# is better than 
for i in range(len(a)):
    
if a is True 
# is better than
if a == True
```
