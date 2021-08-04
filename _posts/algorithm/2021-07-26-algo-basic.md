---
layout: post
current: post
cover:  assets/built/images/author-logo.png
navigation: True
title: first
date: 2021-07-26 16:40:00
tags: [algorithm]
class: post-template
subclass: 'post tag-algorithm'
author: pathfinder357
---
{% include algo-table-of-contents.html %}

### 알고리즘

 알고리즘은 문제의 입력을 수학적이고 논리적으로 정의된 연산과정을 거쳐 원하는 출력을 계
 
산하는 절차이고, 이절차를 c나 python과 같은 언어로 표현하는 프로그램또는 코드가 된다.

입력은 (array(C) 또는 list(Python)), 연결리스트, 트리, 해시테이블, 그래프와 같은 자료의

접근과 수정이 빠른 자료구조에 저장된다.

최초의 알고리즘인 GCD를 재귀를 이용하여 구현한 코드를 짜보았다.
~~~python
def algo_gcd(a,b):
while a*b != 0:
if a>b:
a = a - b
algo_gcd(b ,a % b)
else:
b = b- a
algo_gcd(a, b % a)        
return a + b


print(algo_gcd(22,13))
~~~

