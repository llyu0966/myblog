---
layout: "post"
title: "Probabilistic Modeling"
date:   2020-05-13 1:33:31 -0400
categories: [R]
tags: [Modeling]
redirect_from:
  - /2020/05/13/
---
## Probabilistic Modeling 

Monte Carlo simulation can help find estimates for many probabilities. We will look here at a few examples.

### Example 1

Suppose you generate a sequence of 10 digits, uniformly chosen from the set {0, . . . , 9}. What is the probability that there will be no successive identical digits?

We can simulate the probability that there are successive identical digits as follows:

```{r}
N=1000000
M=10
A=runif(N*M)
dim(A)=c(N,M)
B=floor(10*A)
C=matrix(0,N)
for(i in 1:N) for(j in 2:M)
{if(B[i,j]==B[i,j-1]){C[i]=1}}
sum(C)/M
```
> [1] 61283.1

Note that this implies that the probability that there are no successive identical digits is approximately 1 − 0.612831 = 0.387169. This is very close to the true probability, i.e., (9/10)^9 = 0.3874205.

### Example 2

Suppose a friend offers to play the following game: Your friend will throw a fair 6-sided die 20 times. If the sum is 70, your friend will give you 20 dollars. Otherwise, you give your friend 2 dollars. Should you accept to play the game?

We will estimate the probability that the sum of the digits is exactly 70 by generating many samples of sets of 20 throws of a die and compute the proportion of those that result in a 70:

```{r}
N=1000000
M=20
U=runif(N*M)
dim(U)=c(N,M)
Dice=ceiling(6*U)
SUM=c()
for(i in 1:N) SUM[i]=sum(Dice[i,])
Counter=matrix(0,N)
for (i in 1:N){if (SUM[i]==70) Counter[i]=1}
sum(Counter)/N
```
> [1] 0.05185

This tells us that the probability of getting a sum of 70 is approximately 5.19%, so your expected gains under this game are

0.0519 · 20 + (1 − 0.0519) · (−2) ≈ −0.86.

Since your expected gains for this game are negative, it is probably wiser not to play.
