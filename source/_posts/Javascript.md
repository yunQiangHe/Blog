---
title: Javascript
date: 2019-08-21 23:47:13
categories: javascript
tags:
description: 
---

```
   // var let
    for (var i = 0; i < 10; i++) {
        ((index)=>{
            setTimeout(()=>{
                console.log(index);
            },0)
        })(i)

        // setTimeout是异步执行，也即每一次for循环执行一次，settimeout都会执行一次，但是里面的settimeout并没有立即被执行，而是等到for循环结束，再执行；
        // for循环了10次，就放了10次，当主线程执行完成后，才进入任务队列里面执行。
        // setTimeout(()=>{
        //     console.log(i);
        // },0)
    }
```