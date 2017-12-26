title: 前端常见知识点总结（仅供自己学习记忆用，如果不对之处还请指正，后续不断更新添加）
date: 2017-12-20 14:00:00
description: 
categories:
- web
tags:
- web
toc: true
author:
comments:
original:
permalink: 
---

　　**前言：**这里是我记录的常见（面试和日常）知识点，方便记忆和学习

<!-- more -->

## js部分

### js常见数据类型
- 基本类型：Number、String、Boolean、null、undefined
- 引用类型：Object、Function、Symbol（es6）

### 数组常见的方法

- pop() 方法用于删除并返回数组的最后一个元素。(改变原数组)
- shift() 方法用于把数组的第一个元素从其中删除,并返回第一个元素的值。(改变原数组)
- push() 方法可向数组的末尾添加一个或多个元素，并返回新的长度。(改变原数组)
- unshift() 方法可向数组的开头添加一个或更多元素，并返回新的长度。(改变原数组)
- reverse() 方法用于颠倒数组中元素的顺序。(改变原数组)
- sort() 方法用于对数组的元素进行排序。 (改变原数组)
- splice(规定添加/删除项目的位置,要删除的项目数量,[可选。向数组添加的新项目。]) 方法向/从数组中添加/删除项目，然后返回被删除的项目。(改变原数组)
- slice() 方法可从已有的数组中返回选定的元素。该方法并不会修改数组，而是返回一个子数组。如果想删除数组中的一段元素，应该使用方法 Array.splice()。(不改变原数组)
- concat() 方法用于连接两个或多个数组。(不改变原数组)
- join() 方法用于把数组中的所有元素拼成一个字符串。返回一个字符串。(不改变原数组)
- toString() 方法可把数组转换为字符串，并返回字符串结果。(不改变原数组)
- array1.indexOf(searchElement[, fromIndex])返回某个值在数组中的第一个匹配项的索引。(不改变原数组)
- lastIndexOf() 方法返回指定元素（也即有效的 JavaScript 值或变量）在数组中的最后一个的索引，如果不存在则返回 -1。从数组的后面向前查找，从 fromIndex 处开始。(不改变原数组)
- map() 对数组的每个元素调用定义的回调函数并返回包含结果的数组。(不改变原数组)
- forEach
- filter
- some
- every
- reduce

- ——----------------------------------es6中的
- find
- includes
- 
 