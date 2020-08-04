---
title: 'Python Virtualenv'
date: 2020-03-31 20:00:00
tags:
- Python
- Virtualenv 
---
# Python环境控制

## Motivation
  * package的不断更新迭代，导致一些python课程的实现无法重现
  * 使用tensorflow一类的软件时，1.x版本和2.x版本存在巨大的差异，相当于两套各有千秋的成熟方案。安装两个不同版本的虚拟python环境能有效的减少麻烦。
<!--more-->
## 实现
在命令行窗口
```
pip install virtualenv		#安装virtualenv环境
mkdir any_path			#新建文件夹
virtualenv any_path		#新建虚拟环境
cd any_path/bin			#打开bin文件夹
source activate			#激活虚拟环境
```
激活成功后命令行窗口应该呈现
![实现效果](https://i.loli.net/2020/03/31/6xjWTI14GpyClVB.png)

## python3 实现
先在命令行下查看python3路径
```
which python3
```
一般是`\usr\bin\python3`
随后，将上面的代码简单修改一下
```
pip install virtualenv			#已经安装则忽略这一行
mkdir any_path				#新建文件夹
virtualenv -p \usr\bin\python3 any_path	#新建python3虚拟环境
cd any_path/bin				#打开bin文件夹
source activate				#激活虚拟环境
```

## 退出虚拟环境
在任意位置`deactivate`

## 关于编译器
直接使用`jupyter notebook + python原生`是最简单的方案。
如果使用VSCode等，将python定位到虚拟环境的bin文件夹下的python即可。

## 另外
适用于MAC, Linux, 面向Windows时，尤其在编译器configuration设置上会有诸如环境变量一类的问题。买一个linux云服务器他不香吗？
