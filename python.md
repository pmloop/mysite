---
layout: page
title: Python
permalink: /python/
---

# Python Tricks


## generator for integrals


```python
inte = sum(f(xvec) * xweight)
```
   is much faster than

```python
inte = 0
for i1, xval in enumerate(xvec):
  inte += f(xval) * xweight[i1]
```

## generator for nested sum

cast a nested sum into one big iterator:

* simple case:

```python

N1 = 5
N2 = 8
p1_arr = np.linspace(0.8, 1.2, N1)
p2_arr = np.linspace(3.8, 4.5, N2)

grid = (
        (i1, i2)
        for i1 in range(N1) for i2 in range(N2)
        )

ans = (
        _f(p1_arr[i1], p2_arr[i2])
        for i1, i2 in grid
        )

ans = sum(ans)

```

* if you need further processing:

```python
N1 = 10
N2 = 80
para1_arr = np.linspace(0.8, 1.2, N1)
para2_arr = np.linspace(3.6, 4.0, N2)

grid = (
        (i1, i2)
        for i1 in range(N1) for i2 in range(N2)
        )

pool = [
        [fitfunc([para1_arr[i1], para2_arr[i2]]), i1, i2]
        for i1, i2 in grid
        ]
pool = np.array(pool).T

_ii = np.argmin(pool[0])
i1, i2 = int(pool[1][_ii]), int(pool[2][_ii])

print(para1_arr[i1], para2_arr[i2])
```

## Passing tuple as index for array:

```python
lat[tuple([*xvec, d])]
lat[xvec[0], xvec[1], xvec[2], xvec[3], d]
```


## git basics

Develop locally a version-controlled project:  

(git init to start one)

Then, ssh to a remote,  create an empty vessel:

```unix
git init --bare proj.git
```

Add the remotes locally:

```unix
git remote add tplx tplx:~/olympus/proj.git
```

```unix
git remote add lxpool lxpool:~/<dir>
```

then push your local repo to the remote via:

```unix
git push lxpool
```

To use them, ssh to the remote and 

```
git clone proj.git work_copy
```

You can now do what you want in work_copy.



## adding new columns to old data

```python
new_data = np.row_stack((old_data, col1, col2))
```

why row? because those column at your head is actually row, confusingly enough. 


## filename versioning

```python
filename=f'file_{int(num):03}'
```

## watch out for side effects

```python
y = x**2
x = np.array([1, 2, 3])
```
y is accidentally changed: these are hard bugs to track down. 


## use dictionary method to assess and update global observables


## adding NaN to signal discontinuities

```python
# some condition to decide
iloc = np.argmax(data[2])
# tag: adding nan for discontinuity
data = np.insert(data, iloc, np.nan, axis=1)
```

