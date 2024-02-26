---
layout: post
comments: false
title : Python Tricky
categories: knowlegde-note
date: 2021-06-01 12:00:00

---

```
import numpy as np

a = np.array( [[1,3,4,1],[4,5,6,7], [1,3,4,1], [0,0,0,0]])
for p in a:
    a = []
    print(p)
```
Output:
```
[1 3 4 1]
[4 5 6 7]
[1 3 4 1]
[0 0 0 0]

```

Python has Iterable, Iterator, Generator. Iterable requires to implement the function `__iter__`. Iterator needs both `__iter__` and `__next__`. While Generator is an iterator. Generator contains `yield` or `(xx for in xx expression xx)`. In Python, for keyword will invoke `iter()` function to wrap iteratable objects to be iterators.

Immutable data types: Number, String, Tuple.
Mutable data types: list, dictionary.

Immutable is insensitive to `=`. While, `a = b` operation for mutable data will share the same object, change a/b  will affect another one. Shallow copy: copy(), slice operation, list() and Deepcopy().

Super(xx, self).function() is used to call the parent class function while solve the MRO problem. The problem will mess up programme when parentclass().function() is called.