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
일반적인 프로그램 동작 방식
~~~
A[2]    =      A[2]   +  1
(쓰기)  (대입)  (읽기)   (산술)
~~~



파이썬은 씨언어의 배열의 셀과 다르게 데이터의가 저장된곳의 주소가 저장된다. 

즉 항상 객체의 주소만 저장하기때문에, 리스트의 셀의 크기를 메모리의 주소를 표현 할수있는 8바이트로 고정하면 된다.

모든셀의 크기가 같기 때문에 index에 의해 O(1)시간 접근이 가능하다.

C는 배열에 읽기와 쓰기만 적용되지만 파이썬의 리스트는 pop, insert, append등 여러가지 연산이 추가되는 굉장히 편리

리스트는 용량을 자동조절(동적배열)

ex) def append principle of operation(Pseudo code)

~~~python
def append(A, val):
1. if A.capacity == A.n:  #needed to resize!!
    a. 더큰 메모리를 가진 리스트 B를 할당하고 B.capacity 와 B.n으로 갱신하자  
    b. for i in range(A, n):
        B[i] = A[i]
    c. dispose A
    d. A = B
2. A[n] = val
3. A.n += 1
~~~

#### 리스트가 가지는 강력한 동작들

~~~ python
1.append(val) : #맨 오른쪽(뒤)에 새로운 값 val를 삽입
2.A.pop(i): #A[i]값을 지운후 리턴(i의 오른쪽 값들은 왼쪽으로 한칸씩 당겨져 cell의 수 감소)
3.A.insert(i ,val) : val 연산( 단 A[i] , A[i+1], .. 값들은 오른쪽으로 한칸씩 이동해 A[i]를 비운후 , val 값 저장)
4.A.remove(val) : val값 제거
5.A.index(val) : val 값이 처음으로 등장하는 index 리턴
6.A.count(val) : val값이 몇번 등장하는 지 횟수를 세어 리턴
7.A[i:j] : A[i], ..., A[j-1]까지를 복사해 새로운 리스트 생성하여 리턴(slicing 연산)
8.val in A : 맴버십 연산자 -A에 val가 있으면 True, 없으면 False
~~~



