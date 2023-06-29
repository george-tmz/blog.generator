---
title: "缓存 Cache"
date: 2023-06-28T01:18:13+08:00
draft: true
---

#### 缓存基础
- 通用定义 位于速度相差较大的两种硬件之间，用于协调两者数据传输速度差异的结构 
- 本质 空间换时间
- 为什么用缓存
    1. 提升访问性能
    2. 降低网络拥堵
    3. 减少后端负载
    4. 消除数据库热点
    5. 可预测的性能
    6. 增加系统的可扩展性

#### 缓存的特征指标
##### 命中率
命中率 = 返回正确结果数量/请求缓存次数

命中率越高，缓存使用效率越高

##### 最大空间
缓存中可以存放的最大元素的数量
##### 缓存生存时间TTL
缓存可以存活的时间， 超过时间就消失
##### 缓存清空策略
- FIFO
- LFU
- LRU
- 定时过期
- 懒性过期
- 最长过期
- 最近过期
- 随机过期清理
- 随机清理

#### 常见的几大问题