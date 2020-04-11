---
layout: post
title: Perception Learning Algorithm (PLA) 感知機
categories: [Machine Learning, Deep Learning]
tags: [ML, DL]

---

### PLA 演算法應該可以說是機器學習的class 101

網路上應該已經很多人都有做過類似的解說以及實作。
不過這是我開始學習寫Blog的第一步，請大家手下留情XD
這篇文主要是想提供大家可以簡單看出在3D空間中，PLA是怎麼做到分群的。

就我的認知，PLA是一個分群演算法。
根據過去的資料集，訓練出一套判斷的標準(參數)，針對尚未分群的資料加以歸類。
此演算法只能針對線性可分割的資料做分類。

### 什麼是線性可分割的資料呢 ?

2D平面上，能畫出一條線將資料分成2部分。
3D空間中，能畫出一個面將資料分開。
這部分可以透過下方提供的Source code 來看的出來。


### 原理
神經心理學家Hebb認為學習現象是因為神經元間的突觸產生變化。
感知機是由可調整的鍵結值(weights)以及閥值(threshold)所構成的單一類神經元
![](https://i.imgur.com/CpNnPhd.png)

這可以連結到高中生物課程所說的，要產生一個神經衝動是根據鈉鉀離子的濃度去決定的。
在這裡是透過 "資料"與"鏈結值"丟進Activation function去判斷是否超過threshold去判斷是不是同種資料
![](https://cdn-images-1.medium.com/max/800/1*MofmXIxbv5AOIXHQp_hSOw.png)

Activation function 是可以自由決定的，在本範例單純去判斷算出來的值是不是有大於0

整個PLA的重點在於 "如何修正鍵結值"
"鍵結值的向量" 與 "資料點的向量" 做內積。
設定"分類1"是內積大於0，"分類2"是內積小於0。
如果分類錯誤則透過以下公式來修正鍵結值。
![](http://static.obeobe.com/image/blog-image/machine-learning-foundations-2-6.png)
修正鍵結值的過程中也可以設定"學習率"來調整修正的快慢。





## Ref
> https://medium.com/jameslearningnote/%E8%B3%87%E6%96%99%E5%88%86%E6%9E%90-%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92-%E7%AC%AC3-2%E8%AC%9B-%E7%B7%9A%E6%80%A7%E5%88%86%E9%A1%9E-%E6%84%9F%E7%9F%A5%E5%99%A8-perceptron-%E4%BB%8B%E7%B4%B9-84d8b809f866
> https://blog.fukuball.com/lin-xuan-tian-jiao-shou-machine-learning-foundations-di-er-jiang-xue-xi-bi-ji/
> Coursera 田神




