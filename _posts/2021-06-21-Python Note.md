---
layout: post
comments: false
title : GPUs Server Notes
description: Python Decorator, functools.wraps, functools.update_wrapper, partial differences.
categories: [Knowlegde Note]
---

Decorators: A Python decorator is a specific change to the Python syntax that allows us to add more code to your orginal code.


    def my_decorator(func):
        @wrap(func)
        def wrapper():
            print("Something is happening before the function is called.")
            return func()
        print("Something is happening after the function is called.")
        return wrapper

    @my_decorator
    def say_whee():
        print("Whee!")


`functools.wraps` in fact is equivalent to the combination of `partial()` and `update_wrapper()`.

`t=partial(f, x, z=g)` is used to generate the new '`f`' function `t` with the supplied new positional argument `x` or keyword argument `z`. Meanwhile, new function `t` will lose the orginal details of it, but you can call `update_wrapper(t,f)` to solve this issue. When you are applying decorator, you still can use '@wrap(say_whee)' to keep the `__doc__` and `__name__` of func with it, instead of `wrapper`