---
title: "Numpy"
teaching: 30
exercises: 30
questions:
- "Key question (FIXME)"
objectives:
- "Learn how to create and manipulate multidimensional arrays in numpy"
keypoints:
- "NumPy is the main package for dealing with homogeneous multidimensional arrays. "
---

## The Notebook

The material for this episode is on this notebook:

~~~
3_Numpy [WVU Research Computing].ipynb
~~~
{: .source}

## Exercises

1. Create a vector with 100 zeros, using `sys.getsizeof()` get the size of the array.
Compute the size of the array using the `.size` and `.itemsize` properties and compute the extra overhead of a numpy object.

2. Create an array 5x5 and reorder the rows based on the values of the first column

3. Same as before but ordering the columns based on the order of the first row.

4. Use `numpy.sort()` and check that this function is doing something different from the exercises above.

5. Multiply a 5x3 matrix by a 3x2 matrix (real matrix product)

6. Verify why those two lines produces different results:

```Python
print(sum(range(5),-1))
print(np.sum(range(5),-1))
```

{% include links.md %}
