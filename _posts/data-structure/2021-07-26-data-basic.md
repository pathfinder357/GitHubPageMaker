---
layout: post
current: post
cover:  assets/built/images/author-logo.png
navigation: True
title: 자료구조 (1) 시작
date: 2021-07-26 16:40:00
tags: [data-structure]
class: post-template
subclass: 'post tag-data-structure'
author: pathfinder357
---

순차적 자료구조

(1) 배열, 리스트

인덱스로 임의 원소를 접근

- 연산자 []
- 삽입(append, insert)
- 삭제(pop, remove)

(2) stack, queue, dequeue

- 제한된 접근(삽입, 삭제)  접근만 허용
- 배열과 리스트는 인덱스만 알면 삭제 삽입이 가능하지만 스택, 큐는 제한된 것만 활용가능

＊ 스택 접근 방식
- LIFO(last in first out)
  
밑에서부터 차곡차곡

제한된 연산만 사용하는 자료구조는 굉장히 많다 (ex: )

＊ 큐 접근방식

- FIFO(first in fist out, 선착순)

밑에서부터 차곡차곡

＊ dequeue 접근방식

- stack + queue

(3) Linked List
   
독립적으로 저장되어 있는 노드에 다음값에 대해서 알고있는 링크를연결 하는 것
   
- 각각의 노드에 자기 자신의 val + self.next를 가진다. 
  
- 각자의 값들이 연속되어 있지 않은 곳에 저장되어 있고 다음 노드의 링크를 가지고있는것(idx로 접근 할수가없지만 함수로 가능케 할순있음)





