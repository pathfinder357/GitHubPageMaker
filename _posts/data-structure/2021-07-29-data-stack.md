---
layout: post
current: post
cover:  assets/built/images/author-logo.png
navigation: True
title: 자료구조 (3) stack
date: 2021-07-29 16:40:00
tags: [data-structure]
class: post-template
subclass: 'post tag-data-structure'
author: pathfinder357
---

### stack 
__init(self) : 생성함수
~~~python
def __init__(self):
        self.items = []
~~~

ex)
~~~python
S= Stack()
~~~
init 생성함수안 에있는 객체인 self.itmes = []가 자동으로 생성

try & except : try 블록에 있는것을 수행하다가 수행중 에러가 나오면 except에 있는 statment를 수행
~~~python
def pop(self):
        try:
            return self.items.pop()
        except IndexError:
            print('stack is empty')
~~~

print(len(S)) len 을 수행하면 class Stack 안에 있는 __len__ 안에 있는 statement를 수행
~~~python
def __len__(self):
        return len(self.items)
~~~

stack 안에 수행되는 함수들은 전부 O(1) 상수시간안에 돌아가는 자료구조이다.

prac) 괄호 맞추기

- (2 + 5) * 7 -((3-1)/2+7)
- ( ( ) ( ) )
- ( ( ) ) ) (    <- 적당한 쌍이 아님

-문제:

입력: 왼쪽 오른쪽 괄호의 문자열

출력: 괄호쌍이 맞춰져있으면 True or False

관찰:

......(.......)......

ex1)

( ( ) ( ) )

1 2 2 3 3 1

왼쪽부터 차례로 읽으면

(1) 왼쪽 괄호 ( 왼쪽 괄호가 들어가면 기다려야 하므로 push

ex2)

( ) )

ex3)

( ) (

알고리즘

~~~python
for p in parseq:
    if p =='(' : 
        S.push(p)
    elif p == ')' : 
        S.pop()  # error 오른쪽이 더 많음
    else: 
        print('Not allowed Symbol)
    if len(S) > 0: 
        return False  # error 왼쪽이 더많음
    else: 
        retun True
~~~

전체 소스 코드

~~~python
class Stack:
    def __init__(self):
        self.items = []
    
    def push(self, val):
        self.items.append(val)
    
    def pop(self):
        try:
            return self.items.pop()
        except IndexError:
            print('stack is empty')
    
    #가장 맨위에 있는 값을 리턴    
    def top(self):
        try:
            return self.items[-1]
        except IndexError:
            print('stack is empty')
    
    #stack의 item수 반환
    def size(self):
        return len(self.items)
    
    def paresq(self, p):
        for p in self.items:
            if p == '(':
                self.push(p)
            elif p == ')':
                print('doing pop')
                self.pop(p)
            else:
                print('not allowed Symbol')
        if self.__len__() > 0:
            return False
        else:
            return True
  
~~~

### postfix 변환기

~~~python
from stack_queue import Stack

def postfix_op(x):
    s = Stack()
    outstack=[]
    priority = {
        '*':3,
        '/':3,
        '+':2,
        '-':2,
        ')':4,
        '(':1
    }
    for token in x:
        if token not in '+-*/()':
            outstack.append(token)
        elif token == '(':
            s.push(token)
        elif token == ')':
            while s.top() != '(':
                outstack.append(s.pop())
            s.pop()
        else:
            if s.is_empty():
                s.push(token)
            else:
                while s.size() > 0:
                    if priority[s.top()] >= priority[token]:
                        outstack.append(s.pop())
                    else:
                        break
                s.push(token)
    while not s.is_empty():
        outstack.append(s.pop())
    return outstack
~~~







