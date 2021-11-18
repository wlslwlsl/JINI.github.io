---
date: 2021-11-18
title: "Zero-Shot Learning"
subtitle "Zero-Shot Learning 이란?"
categories: 기계학습
tags:
  - image
  - zero-shot learning
  - few-shot learning
  - one-shot learning
  - 소량
  - 레이블

# 목차
toc: true  
toc_sticky: true 
---




## 기본개념

<center>**Zero-Shot Learning**</center>

<center><u>**데이터를 보지 않아도 분류 가능하도록 학습하는 것**</u></center>

인공지능이든 기계학습이든 데이터는 중요하다. 

막상 현실의 문제는 데이터는 많아도 양질의 데이터로 뽑아내기 힘든 것..

소량의 데이터로 이미지 분류하는 논문을 작성한 적이 있는데, 이 부분도 광범위한 데이터를 양질의 데이터로 전처리하는 것이 시간적 여유가 되지 않아서 생각하게 된 아이디어다.

​이러한 현실 문제와 한계를 해결할 수 있는 것이 zero-shot learning 인 것 같아 관심을 가지게 되었다. 


​
## Zero-Shot Learning 이란?

**일반적인 사람의 능력을 학습으로 바꾼것이며 전이학습에서 발전된 기계학습의 한 종류이다. **

**즉, <u>데이터 간의 관계와 공통점으로 정답을 찾는 것!</u>**

## 특징

1. 데이터가 없어도 양질의 패턴이나 결과를 도출할 수 있다.

2. label 값을 따로 지정하지 않아도 분류가 가능

> Ex. 강아지 데이터를 통해 강아지 클래스를 학습하였는데 고양이 사진을 넣었다. 그럼 기존 인공지능의 경우는 분류하지 못하거나 유사도를 낮추며 강아지 클래스로 갈 것이다. 이러한 경우 제로샷 러닝은 고양이라는 클래스를 생성하는 것. 