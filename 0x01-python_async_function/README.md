<p align="center">
    <img align="center" src="https://github.com/tivereidoro/assets/assets/105525310/8d298662-9874-46b0-aabc-54f837bcc6a4" alt="alx_swe" width="60"  height="60"/>
</p>

---
<div align="center">

## 0x01. PYTHON - ASYNC
<img src="https://img.shields.io/badge/Python-306998"> &nbsp;<img src="https://img.shields.io/badge/Back-end-eed718">
</div>

<div align="center">
    <img align="center" alt="header" width="90%" src="https://github.com/tivereidoro/alx-backend-python/assets/105525310/65f0ba4a-b904-455a-a217-a43f33215880"/>
</div>

---
### Resources (Read or watch):
* [Async IO in Python: A Complete Walkthrough](https://realpython.com/async-io-python/)
* [asyncio - Asynchronous I/O](https://docs.python.org/3/library/asyncio.html)
* [random.uniform](https://docs.python.org/3/library/random.html#random.uniform)

### General Requirements
* A `README.md` file, at the root of the folder of the project, is mandatory
* Allowed editors: `vi`, `vim`, `emacs`
* All your files will be interpreted/compiled on Ubuntu 18.04 LTS using `python3` (version 3.7)
* All your files should end with a new line
* All your files must be executable
* The length of your files will be tested using `wc`
* The first line of all your files should be exactly `#!/usr/bin/env python3`
* Your code should use the `pycodestyle` style (version 2.5.x)
* All your functions and coroutines must be type-annotated.
* All your modules should have a documentation (`python3 -c 'print(__import__("my_module").__doc__)'`)
* All your functions should have a documentation (`python3 -c 'print(__import__("my_module").my_function.__doc__)'`
* A documentation is not a simple word, it’s a real sentence explaining what’s the purpose of the module, class or method (the length of it will be verified)

### Tasks 🎯
### 0. The basics of async: [0-basic_async_syntax.py](0-basic_async_syntax.py)
Write an asynchronous coroutine that takes in an integer argument (`max_delay`, with a default value of 10) named `wait_random` that waits for a random delay between 0 and `max_delay` (included and float value) seconds and eventually returns it.

Use the `random` module.
```groovy
bob@dylan:~$ cat 0-main.py
#!/usr/bin/env python3

import asyncio

wait_random = __import__('0-basic_async_syntax').wait_random

print(asyncio.run(wait_random()))
print(asyncio.run(wait_random(5)))
print(asyncio.run(wait_random(15)))

bob@dylan:~$ ./0-main.py
9.034261504534394
1.6216525464615306
10.634589756751769
```

### 1. Let's execute multiple coroutines at the same time with async: [1-concurrent_coroutines.py](1-concurrent_coroutines.py)
Import `wait_random` from the previous python file that you’ve written and write an async routine called `wait_n` that takes in 2 int arguments (in this order): `n` and `max_delay`. You will spawn `wait_random` `n` times with the specified `max_delay`.

`wait_n` should return the list of all the delays (float values). The list of the delays should be in ascending order without using `sort()` because of concurrency.
```groovy
bob@dylan:~$ cat 1-main.py
#!/usr/bin/env python3
'''
Test file for printing the correct output of the wait_n coroutine
'''
import asyncio

wait_n = __import__('1-concurrent_coroutines').wait_n

print(asyncio.run(wait_n(5, 5)))
print(asyncio.run(wait_n(10, 7)))
print(asyncio.run(wait_n(10, 0)))

bob@dylan:~$ ./1-main.py
[0.9693881173832269, 1.0264573845731002, 1.7992690129519855, 3.641373003434587, 4.500011569340617]
[0.07256214141415429, 1.518551245602588, 3.355762808432721, 3.7032593997182923, 3.7796178143655546, 4.744537840582318, 5.50781365463315, 5.758942587637626, 6.109707751654879, 6.831351588271327]
[0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
```
The output for your answers might look a little different and that’s okay.

### 2. Measure the runtime: [2-measure_runtime.py](2-measure_runtime.py)
From the previous file, import `wait_n` into `2-measure_runtime.py`.

Create a `measure_time` function with integers `n` and `max_delay` as arguments that measures the total execution time for `wait_n(n, max_delay)`, and returns `total_time / n`. Your function should return a float.

Use the `time` module to measure an approximate elapsed time.
```groovy
bob@dylan:~$ cat 2-main.py
#!/usr/bin/env python3

measure_time = __import__('2-measure_runtime').measure_time

n = 5
max_delay = 9

print(measure_time(n, max_delay))

bob@dylan:~$ ./2-main.py
1.759705400466919
```

### 3. Tasks: [3-tasks.py](3-tasks.py)
Import `wait_random` from `0-basic_async_syntax`.

Write a function (do not create an async function, use the regular function syntax to do this) `task_wait_random` that takes an integer `max_delay` and returns a `asyncio.Task`.
```groovy
bob@dylan:~$ cat 3-main.py
#!/usr/bin/env python3

import asyncio

task_wait_random = __import__('3-tasks').task_wait_random


async def test(max_delay: int) -> float:
    task = task_wait_random(max_delay)
    await task
    print(task.__class__)

asyncio.run(test(5))

bob@dylan:~$ ./3-main.py
<class '_asyncio.Task'>
```

### 4. Tasks: [4-tasks.py](4-tasks.py)
Take the code from `wait_n` and alter it into a new function `task_wait_n`. The code is nearly identical to `wait_n` except `task_wait_random` is being called.
```groovy
bob@dylan:~$ cat 4-main.py
#!/usr/bin/env python3

import asyncio

task_wait_n = __import__('4-tasks').task_wait_n

n = 5
max_delay = 6
print(asyncio.run(task_wait_n(n, max_delay)))

bob@dylan:~$ ./4-main.py
[0.2261658205652346, 1.1942770588220557, 1.8410422186086628, 2.1457353803430523, 4.002505454641153]
```

<!--<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>-->

<!--
# REFERENCE 📚
## 1. YOUTUBE VIDEOS 🎥
a. [YOU-TUBE VIDEO BY Tech With Tim](https://www.youtube.com/watch?v=t5Bo1Je9EmE) 📹

b. [YOU-TUBE VIDEO BY Socratica](https://www.youtube.com/watch?v=K56nNuBEd0c) 📹

---

## 2. HINT for Python Async project
**only if you stuck, keep googling🙂**
### Task0:
* **random.uniform(a, b)** function returns a random floating point number N such that a <= N <= b for a <= b and b <= N <= a for b < a.
* **asyncio.sleep()** is a function in Python's asyncio library that pauses the execution of the current coroutine for a specified amount of time. It's like a pause or sleep command for asynchronous code.


### Task1 :
* **asyncio.create_task()** is like saying "Start this task in the background, and give me an object that I can use to check on the task's status or get its result later."
* **asyncio.gather()** is like saying "I have these tasks that can run at the same time. Start them all and give me all their results when they're done."
* **asyncio.as_completed()** this can help avoid using sorted()
* **sort() vs sorted()**:
    * sort() and sorted() are both built-in functions in Python that can be used to sort a list.
    * **Method vs Function**: sort() is a method that can only be used with lists. sorted() is a function that accepts any iterable.
    * **In-place vs New List**: sort() sorts the list in-place, meaning that it modifies the original list and returns None. sorted() returns a new sorted list.


### Task2:
* time.time(): Returns the time in seconds since the epoch (start point). Used for real-world timing.
* time.perf_counter(): Returns the highest-resolution timer for short durations. Includes sleep time. Used for performance testing.
* time.process_time(): Returns the sum of system and user CPU time of the current process. Doesn't include sleep time. Used for process time measurement.
* **asyncio.run()** is like saying "Start this task and wait for it to finish, then give me the result." It takes care of creating an event loop, running the given coroutine in the loop, and closing the loop when the coroutine is done.

**Task3 & Task4 we gonna use same thing we did use before...**

### Reaction from Peers:
> For task1 there's a way to do it without using sort ot sorted

> They said dont use sort(), so sorted() is working fine, if you dont want to use sorted, maybe u can do bubble sort with 2 for loop or other sorting algorithm

> No we can use something else like create list tasks and iter throw it using as_completed cuz as_completed return the earliest so it sort the result. My English not that good but see this method accept list and give you a sorted list of tasks

![Screenshot from 2024-01-16 08-37-53](https://github.com/elyse502/alx-backend-python/assets/125453474/b38ffddc-288b-4b57-8616-398d3dc2f836)

> I wasn't aware of it, that really smart, so instead of using asyncio.gather , asyncio.as_completed will give us sorted result

> But you have to run the tasks by your self as_completed will not run it for you

**Continuity of the conversation** 👉 [LINK](https://discord.com/channels/1148581179084243054/1196519679565496320)
-->

---

#### Code Editor used: Mostly `VS-Code`; also  `Vim`
##
#### AUTHOR 👨🏽‍💻:
[Tivere IDORO](https://github.com/tivereidoro)

<hr>
