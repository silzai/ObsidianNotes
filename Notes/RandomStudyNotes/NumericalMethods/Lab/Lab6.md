- Solving system of equations:
- first define the coefficient matrix A and column vector b 
- To quickly find the unknowns/solution:
```java
x = inv(A)*b;
//or can use left division is same as inversing
x = A\b;
```
- Cramer's rule:
```java
A = [ 3 -0.1 -0.2; 0.1 7 -0.3; 0.3 -0.2 10];
b = [7.85; -19.3; 71.4];
//finding determinant of original matrix A
D = det(A);
//replacing first column of A with column vector b
A(:, 1) = b;
//finding x1 using cramers rule formula
x1 = det(A)/D
x1 = 3.0000
//converting modified A back to the original matrix A 
A(:, 1) = [3; 0.1; 0.3];
//replacing second column of A with column vector b
A(:, 2) = b;
//finding x2 using cramers rule formula
x2 = det(A)/D
x2 = -2.5000
```
- LU decomposition: 
- first decompose into L and U by:
```
[L, U] = lu(A);
```
	- to divide 2 matrices, for example in 
```java
[L]{d} = {b}
```
- To find `{d}`, we will do left division i.e. `\` , this inverses the division as opposed when using normal division i.e. `/` or `inv()` which does the same thing

## Excel: 
To find solutions to linear equations, Ax=b using excel:
- Define matrix A and column vector b in cells
- then to find inverse of A, select any random empty cells, then type "= MINVERSE()"
- then select the cells of matrix A to generate inverse of A
- Then to multiply A^-1 and b, in other random cells of the size of b, type "=MMULT()"
- then for the first argument, select the cells of A^-1, then for second argument select the cells of b

To find solution to non-linear equations:
- Will do it using solver like in lab 5, but will make a new cell called "sum=" and it will be the sum of the outputs of both the equations, and in solver, "sum=" should be set objective equal to 0, and also solutions of equations should be constraints equal to 0.

To do bisection method:
- first create the titles for the table, then insert values of xl, xu, xr and fl, fu, fr, in that order, so we can drag to get the respective values easily
- Then for the next xl and xu, put if conditions 

