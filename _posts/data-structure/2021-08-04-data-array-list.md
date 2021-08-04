---
layout: post
current: post
cover:  assets/built/images/author-logo.png
navigation: True
title: 자료구조 (1) 어레이와 리스트 차이
date: 2021-08-03 12:40:00
tags: [data-structure]
class: post-template
subclass: 'post tag-data-structure'
author: pathfinder357
---

{% include data-table-of-contents.html %}

### 배열과 리스트
파이썬은 씨언어의 배열의 셀과 다르게 데이터의가 저장된곳의 주소가 저장된다. 

즉 항상 객체의 주소만 저장하기때문에, 리스트의 셀의 크기를 메모리의 주소를 표현 할수있는 8바이트로 고정하면 된다.

모든셀의 크기가 같기 때문에 index에 의해 O(1)시간 접근이 가능하다.

C는 배열에 읽기와 쓰기만 적용되지만 파이썬의 리스트는 pop, insert, append등 여러가지 연산이 추가되는 굉장히 편리

리스트는 용량을 자동조절(동적배열)

ex) how to append operation

~~~python
A.append(x)"
if A.n < A.capacity:
A[n] = x
A.n = n +1
else: (A.n == A.capacity)
B = A.capacity *2 (새로 할당)
for i in range(n):
B[i] = A[i]
del A
A = B
A[n] = x
A.n = n+1
~~~



