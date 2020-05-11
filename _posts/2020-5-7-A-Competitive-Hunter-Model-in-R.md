---
layout: post
title:  "A Competitive Hunter Model in R"
date:   2020-05-07 1:33:31 -0400
categories: R
---
## Using Euler's Method for Systems in R

Example: A Competitive Hunter Model

Assume we have a lake that is stocked with both bass and trout. Because both eat the same food sources, they are competing for survival. Let b(t) and T(t) denote the bass and trout populations, respectively, at time t. The rates of growth for bass and for trout are estimate by the differential equations

dB/dt = B・(10 - B - T), B(0) = 5

dT/dt = T・(15 - B - 3・T), T(0) = 2

Use Euler's method with step size ∆t=0.1 to estimate the solotion curves from 0≤t≤7 for (a) B(t) versus t; (b) T(t) versus t; (c) The solution trajectory (B(t), T(t)) in the phase plane.

We implement this in R as follows:

## (a) B(t) versus t


```{r}
DE1=function(a,b) return(a*(10-a-b))
DE2=function(a,b) return(b*(15-a-3*b))
ICt=0
ICx=5
ICy=2
t=c()
Bass=c()
Trout=c()
DERIV=c(DE1(ICx,ICy),DE2(ICx,ICy))
t[1]=ICt
Bass[1]=ICx
Trout[1]=ICy
step.size=0.1

for(i in 2:71){
   t[i]=t[i-1]+step.size
   Bass[i]=Bass[i-1]+step.size*DERIV[1]
   Trout[i]=Trout[i-1]+step.size*DERIV[2]
   DERIV=c(DE1(Bass[i],Trout[i]),DE2(Bass[i],Trout[i]))}
plot(t,Bass, type="l")
   
```
![](https://llyu0966.github.io/mypic/BT/BC.png)

## (b) T(t) versus t


```{r}
plot(t, Trout, type="l")
```
![](https://llyu0966.github.io/mypic/BT/TC.png)

## (c) The solution trajectory (B(t), T(t)) in the phase plane.

You can also embed plots, for example:

```{r}
plot(Bass, Trout, type="l")
```
![](https://llyu0966.github.io/mypic/BT/BTC.png)

```{r}
data.frame(cbind(t,Bass,Trout))
```
![](https://llyu0966.github.io/mypic/BT/BT1.png)
![](https://llyu0966.github.io/mypic/BT/BT2.png)
