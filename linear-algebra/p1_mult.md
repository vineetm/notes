### Matrix Multiplication and Column Space

* [Link](https://ocw.mit.edu/courses/res-18-010-a-2020-vision-of-linear-algebra-spring-2020/resources/the-column-space-of-a-matrix/)


#### Column Space of a Matrix

* Given a matrix A, view it only in terms of its columns. For example:
  
  ```
  A = [
    1 4 5
    3 2 5
    2 1 3
  ]
  ```

  has three columns:

  ```
  c1 = [
    1 
    3 
    2
  ]

  c2 = [
    4
    2
    1
  ]

  c3 = [
    5
    5
    3
  ]
  ```

  * If we multiply this matrix by a column vector X, we get linear combinations of the columns of A:

  ```
  x  = [
    x1
    x2
    x3
  ]
  ```

  ```
  Ax = 
    x1[ 
      1
      3
      2
    ] 
    + 
    x2[
      4
      2
      1
    ] +
    x3[
      5
      5
      3
    ]
  ```


* C(A): all linear combinations of the columns of A. As we only have two independent columns, C(A) is a plane.


#### Matrix Multiplication
* The above matrix can be represented in terms of `CR`

* To obtain C, we remove the dependent column `c3`, as its a linear combination of `c1` and `c2`:
```
C = [
  1 4
  3 2
  2 1
]
```
* R can be constructed by thinking how the columns in `C` are picked to obtain `A`. To construct the first column of `A`, we only need the first column of C. For the last column of C, we add first and second columns of `C`
```
R = [
  1 0 1
  0 1 1
]
```

#### Column and row rank
* As `C` has only two columns, the column rank of `C` is 2
* Column rank will always be equal to the row rank