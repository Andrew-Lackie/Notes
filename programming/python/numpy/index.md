# Numpy

NumPy is the fundamental package for scientific computing in Python. It is a Python library that provides a multidimensional array object, various derived objects (such as masked arrays and matrices), and an assortment of routines for fast operations on arrays, including mathematical, logical, shape manipulation, sorting, selecting, I/O, discrete Fourier transforms, basic linear algebra, basic statistical operations, random simulation and much more. 


## Import

```python
import numpy as np
```

## Data Types

* i - integer
* b - boolean
* u - unsigned integer
* f - float
* c - complex float
* m - timedelta
* M - datetime
* O - object
* S - string
* U - unicode string
* V - fixed chunk of memory for other type ( void )

#### Check type 

```python
arr.dtype
```

## Arrays

#### 1-D

```python
arr = np.array([1, 2, 3, 4, 5])
```
#### 2-D

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
```
#### Dimensions

```python
arr.ndim
```
#### Indexing

##### First element
```python
arr[0]
```
##### Second element on first row

```python
arr[0,1]
```
#### Slicing

```python
arr[1:5:2] #slice every other index 1 to 5 
```
### Methods

#### clip()
This function is used to Clip (limit) the values in an array.

```python
numpy.clip(a, a_min, a_max, out=None)

# Example

in_array = [1, 2, 3, 4, 5, 6, 7, 8 ]
out_array = np.clip(in_array, a_min = 2, a_max = 6)
print(out_array)
# outputs: [2 2 3 4 5 6 6 6]
```

