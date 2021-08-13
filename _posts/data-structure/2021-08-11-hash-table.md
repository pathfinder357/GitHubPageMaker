---
layout: post
current: post
cover:  assets/built/images/author-logo.png
navigation: True
title: 자료구조 (7) 해시 테이블
date: 2021-08-11 12:40:00
tags: [data-structure]
class: post-template
subclass: 'post tag-data-structure'
author: pathfinder357
---

### Hash Table

***
1. 해시 테이블은 일종의 사전이고, Python 의 dict 자료구조처럼 다음 연산을 빠르게 지원 
   1. if(데이터가 key, value 값의 쌍으로 구성
      * insert(key, val)     #(key, val)를 해시 테이블에 저장, 같은 키가 있다면 overwirte 
      * remove(key, val)     #(key, val)가 해시 테이블에 있다면 제거(delete)
      * search(key)          #(key, val)를 찾아 리턴, 없다면 알려줌

2. 해시 테이블은 보통 정보를 담아 저장할수있는 서랍장 행태로 구현
    
    * 가장 핵심적인 과정은 각 정보를 몇번째 서랍에 넣을지를 결정하는 것
    
3. 정보 K(key)가 저장될 서랍장(slot) 번호를 계산하는 함수 f()를 hash func 이라 한다.

***
#### hash func

 * 만약 key값이 정수가 아니라면?> 실수이거나 문자열이라면?
    * (실수, 문자열) key 값을 정수에 대응시키는 prehash함수를 먼저 사용해 변환
    
    * __hash__ 함수로 지정할수 있음
    
* perpect 해시 함수: 충돌없이 1 - to - 1 매핑하는 해시 함수

* c- universal 해시 함수: 서로 임의의 두 key 값 x, y 에대해 prob(f(x) == f(y)= c/size(H))
    이 성립하는 해시 함수

* (key 값이 숫자일 경우)
   * Division: f(k) = (k mod p) mod m(p:소수)
      * key 값들의 성질이 잘 알려지지 않은 경우
   
   * Multiplication: f(k) = ((ak) mod 2^w) >> (w-r)
      * a:랜덤값, w =log k, r=log m
   
   * folding: key값들의 digit을 나눠 연산하는 방식
      * shift - folding: ex) bank- account k = 1234 - 567 - 601 두개의 digit 씩 나눠 모두 
         더한다 -> (12+ 34+ 56+ 76+ 01) mod m
   
   * mid - square : key 값을 적당히 연산후 , 그결과의 중간부분을 떼어내 주소로 사용
      * m= 1000이고, k= 3121이면, 3121 ^2 = 9740641이되고 중간에 3 digit을 때어낸 주소 406
   
   * Extraction: key 값의 각 파트마다 임의의 digit을 떼어네 연결해 계산
      * 계좌번호가 1254-387-601이라면, 1254에서 12, 601에서 1을 때어낸후 서로 붙여 121을 만듬
   
* (key 값이 string 경우)

   * Additive hash: key[i]의 단순 합
   * Rotating hash: <<, >>(비트 쉬프트)연산과 ^(exclusive or) 연산을 반복
   
* 좋은 해시 함수란?
   * 되도록 빠르고, 충돌이 되도록 적어야 한다.

***

#### 충돌 해결 방법
   * 서로 다른 key 값 x, y에 대해 f(x) = f(y)가 된다면 두 키값은 충돌이라함
   * 이와 같은 경우에 두값을 해시 테이블에 저장 방법 즉 충돌 해경방법 필요
   * open - addressing 과 chaining 두가지 방법이 일반적임
   
a. open addressing: linear probing
* 삽입 탐색 pseudo code ↓

~~~python
def set(key, val):
   i = find_slot(key)      #빈 슬롯이 없는 경우 대책은?
   if i == FULL:           #더 큰 테이블이 필요함.
      return None
   if H[i] is occupied:    #key값이 존재하면 기존 값 수정
      H[i].val = val       #val 값 update 후 리턴
   else:                   #H[i]가 비어있는 경우, 즉 key가 없다면 새로 지정해야함
      H[i].key =key
      H[i].val = val
   retrun key

def find_slot(key):
   i = f(key)
   start = i
   while (H[i] is occupied) and (H[i].key != key):
      i = (i+1) % m
      if i == start: 
         return FULL
      return i
~~~

* 삽입 연산: set(key, val)
    1. 해시 테이블 H의 각 슬롯에는 하나의 아이템을 저장
    2. 아이템(key , val) 쌍으로 정의
    3. key는 아이템들끼리 구분하므로 아이템마다 서로 달라야함
    4. value 는 해당 아이템의 다양한 정보를 의미
    5. key 값을 갖는 아이템이 이미 테이블에 있다면 해당 아이템의 val를 매개변수 val값으로 수정, 없다면 새 아이템(key, val)를 삽입하는 연산
    6. 정상적으로 삽입이 이루어지면, key 값을 그대로 리턴하고, 빈테이블에 빈슬롯이 없어 삽입하지 않으면 FULL 리턴
    7. 이를 위해 open addressing 방법에 따라 key값을 갖는 아이템을 찾거나 빈슬롯을 찾아 H인덱스를 리턴하는 find_slot(key)함수 필요
* find_slot(key)
    8. key 값을 갖는 아이템을 찾아 index를 리턴. 단 해당 슬롯에 아이템 있다면 key 값을 갖는 아이템이며, 슬롯이 비어있다면 해당 아이템이 해시 테이블에 없다는 뜻
    9. 만약 key 값을 갖는 슬롯이 존재하지도, 빈슬롯도 없다면 FULL리턴

* 삭제 psuedo code ↓
~~~python
def remove(key):
    i =find_slot(key)
    if H[i] is unoccupied:
        return None
    j = i
    while True:
        mark H[i] as unoccupied
        while True:
            j = (j+1) % m 
            if H[j] is unoccupied:  # 이동완료
                return key
            k = f(H[j].key)
            if not(i < k <= j or j <i< k or k<=j <i):
                break
        H[i] = H[j]
        i = j
~~~

* 삭제 연산: remove(key)
    1. key 값을 갖는 아이템을 find_slot()을 이용해 찾는다. 
    2. H[i]가 비었다면 삭제할 아이템이 실제로 존재 하지않으므로 None 리턴
    3. H[i]가 존재한다면, 이 아이템때문에 밀린 아래쪽의 cluster 들을 연쇄적으로 위로 올려 이동한다
    4. 이동한후 성공적인 삭제가 수행되었다는 의미에서 key 값 자체 리턴
        * H[i]는 현재 빈슬롯이고, 아래쪽 H[j]에 있는 아이템을 H[i]로 이동할지를 결정해야 함
        * H[j].key 값의 해시 함수 값을 k 라 하자 즉, k = f(H[j].key)이다
        * 이 키 값이 [i,j]에 있다면 즉, (..i..k..j..)순이라면 H[j]를 H[i]로 옮기면 안됨
        * 왜?? ->  


