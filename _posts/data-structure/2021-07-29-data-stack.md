---
layout: post
current: post
cover:  assets/built/images/author-logo.png
navigation: True
title: 자료구조 stack(2)
date: 2021-07-29 16:40:00
tags: [data-structure]
class: post-template
subclass: 'post tag-data-structure'
author: pathfinder357
---

### stack 

~~~python
class Stack:
    def __init__(self):
        self.top=[]

    def __len__(self):
        return len(self.top)
    
    def __str__(self):
        return str(self.top[::1])

    def push(self, item):
        self.top.append(item)

    def is_empty(self):
        if self.top==0:
            return True
        else:
            return False

    def pop(self):
        if not self.is_empty():
            return self.top.pop(-1):
        else:
            print("stack underflow")
            exit()
    def clear(self):
        self.top[]
~~~






