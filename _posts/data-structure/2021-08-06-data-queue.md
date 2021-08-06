---
layout: post
current: post
cover:  assets/built/images/author-logo.png
navigation: True
title: 자료구조 (2) 순차적자료구조
date: 2021-08-06 11:33:00
tags: [data-structure]
class: post-template
subclass: 'post tag-data-structure'
author: pathfinder357
---

## Queue

#### FIFO(first-in first-out)규칙의 순차적 자료구조

자료를 추가 / 삭제하는 통상적으로 합의한 용어

insert -> enqueue

delete -> dequeue

이런식으로 작동할려면 어떻게 해야할까?

stack은 어디까지 쌓여있는지에 대한 정보 즉 top()에 있는 값의 인덱스만 가지고 작동을 다루었다면

queue는 1.enqueue는 차곡차곡 쌓여서 어디까지 쌓여있는지

2.dqueue 가장 밑에 있는 다음에 나갈 값이 어디 인덱스가 있는지 즉 두개의 인덱스 이 두개로 문제를 해결.

여기서 주의할점은 dequeue를 한다고 해서 실제로 값이 삭제되는 것이 아니고

index를 조절하는것일 뿐이다.

#### Josephus Problem

~~~python
from stack_queue import Queue

def rullet(n,k):
    Q=Queue()
    for cnt in range(1, n+1):
        Q.enqueue(cnt)
    while Q.size !=0:
        for i in range(1,k):
            Q.enqueue(Q.dequeue())
        Q.pop()
    return Q.dequeue()
~~~








  





