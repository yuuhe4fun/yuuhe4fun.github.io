---
layout: archive
title: ""
permalink: /research/
author_profile: true
---

# Research Experience

## *I. Research on human counting based on channel state information (CSI) measurements*
**Supervisor:** [Prof. Yijie Xun](https://teacher.nwpu.edu.cn/xunyijie.html)
**Date:** Dec. 2021 ~ April. 2022

Human counting, which means counting or accurately estimating the number of people with a given region, is of vital significance in many people-centric Internet of Things (IoT) applications. Traditional counting methods have inherent shortcomings, including privacy concerns, high deployment costs and low accuracy. Recent years, some schemes based on Wi-Fi perception have been proposed.

In this research, we proposed a device-free scheme which could be proven to get high counting accuracy in indoor environments. We utilized the [CSI tool](https://dhalperi.github.io/linux-80211n-csitool/) to extract CSI values from the receiver end (Fig. 1 (a)) which is equipped with a commercial wireless network card, while the transmitter like a router (Fig. 1 (b)) continuously sends Wi-Fi packets to receiver. 

<center>
    <img style = "
        border-radius: 0.3125em;
        box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
        src = "../images/intel5300NUC.jpg" 
        width = "48%"
        >
    <img style = "
        border-radius: 0.3125em;
        box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
        src = "../images/tplink_n600.jpg" 
        width = "48%"
         >
    <br>
    <div style = "
        color: orange;
        border-bottom: 1px solid #d9d9d9;
        display: inline-block;
        color: #999;
        padding: 2px;">
        Fig. 1 (a): YM-03 NUC; Fig. 1 (b): TPLink N600 router
    </div>
    <p> </p>
</center>

For different models of wireless network cards, $n$ is different from each other, which means each Wi-Fi link has $n$ subcarriers. Therefore we can obtain $n$ subcarriers and each subcarrier refers to the properties of wireless link. Owing to the transmitter ($T_{x}$) has $x$ antennas and receiver ($R_{x}$) has $y$ antennas, the CSI matrix M for each packet can be expressed as follows:

$$
\left(\begin{array}{cccc}
M_{1,1} & M_{1,2} & \cdots & M_{1, n} \\
M_{2,1} & M_{2,2} & \cdots & M_{2, n} \\
\vdots & \vdots & \ddots & \vdots \\
M_{x \times y, 1} & M_{x \times y, 2} & \cdots & M_{x \times y, n}
\end{array}\right)
$$

In our experimental settings, $x$ = 3, $y$ = 1, and $n$ = 30. 
The indoor counting scenario based on CSI measurements can be shown roughly below.

<center>
    <img style = "
        border-radius: 0.3125em;
        box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
        src = "../images/scene.png" >
    <br>
    <div style = "
        color: orange;
        border-bottom: 1px solid #d9d9d9;
        display: inline-block;
        color: #999;
        padding: 2px;">
        Fig. 2 Indoor counting scenario based on CSI measurements
    </div>
    <p> </p>
</center>

After collecting and extracting the CSI values from packets, we chose the amplitude information for further process. And we chose two algorithms to remove the noise
components and retain the main data features: ***Hampel Filter Denoising*** and ***Discrete Wavelet Transform Denoising***. When we completed further data process, we built a LSTM training model to achieve the classification of human number, which is shown below.


<center>
    <img style = "
        border-radius: 0.3125em;
        box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
        src = "../images/model.png" >
    <br>
    <div style = "
        color: orange;
        border-bottom: 1px solid #d9d9d9;
        display: inline-block;
        color: #999;
        padding: 2px;">
        Fig. 3 The work flow of our LSTM training model 
    </div>
    <p> </p>
</center>

We conducted human counting experiments in different settings. Here is one of the confusion matrices of crowd counting accuracy in the hall environment (<font color=red>Stand still</font>, <font color=brown>Walk regularly</font>, <font color=blue>Walk around randomly</font>)

<center>
    <img style = "
        border-radius: 0.3125em;
        box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
        src = "../images/demo.png" >
    <br>
    <div style = "
        color: orange;
        border-bottom: 1px solid #d9d9d9;
        display: inline-block;
        color: #999;
        padding: 2px;">
        Fig. 4 The confusion matrix of crowd counting accuracy 
    </div>
    <p> </p>
</center>

