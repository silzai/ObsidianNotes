- previous methods are not appropriate to find roots if we have many equations
- so to model the set of simultaneous equations, we will use matrices
- we can write the matrices as: $$[A]\{X\}=\{B\}$$
- and then $x$ will be: $$\{X\}=[A]^{-1}\{B\}$$
- where $$\{X\}=\begin{bmatrix} x_1 \cr x_2 \cr \vdots \cr x_n \end{bmatrix}$$
- the $x$'s are different variables, i.e. x, y etc.
- there are 3 types ways to solve these linear system of equations:
	- Gaussian elimination
	- LU factorization & Matrix inversion
	- Iterative methods

## Gaussian Elimination

- *If we have n<=3 where n is the number of equations; we can use these 3 methods below:*
### Graphical Method:
- there is problem, when the equations do not intersect
### Cramer's rule:
- Method for finding unknowns using Cramer's rule is given in slide 12, but also summarized below:
- can use rule of Sarrus to find the determinant of $3\times3$ matrices.
- where: $$x_1=\frac{\begin{vmatrix} b_1 \space x_{12} \space x_{13} \cr b_2 \space x_{22} \space x_{23} \cr b_3 \space x_{32} \space x_{33}\end{vmatrix}}{D}, x_2=\frac{\begin{vmatrix} x_{11} \space b_1 \space x_{13} \cr x_{21} \space b_2 \space x_{23} \cr x_{31} \space b_3 \space x_{33}\end{vmatrix}}{D}, ...$$
- and where, $D = | A |$

### Elimination of unknows:
- Method to find unknows is given on slide 16.

- *Now for methods where n>3:*
### Naïve Gauss Elimination:
- First convert the matrix to REF (Row Echelon Form) using elementary row operations.
- and then do backward substitution
- to improve gaussian elimination:
	- arrange the equations so that the earlier equations have greatest constants (pivot elements) i.e. we will change the position of the equations
	- partial pivoting: interchange only rows, for this we will take absolute value of all elements in columns, and then interchange the row with the largest first element.
	- complete/full pivoting: also interchange columns (rarely used because also have to change the variable orders)
### Gauss-Jordan Elimination:
- steps given from slide 3. next ppt.

## LU decomposition & Matrix Inversion:
- LU means lower; upper
- since Gaussian elimination is slow in some instances, we will use this one
- steps for LU decomposition:
	- Given the form $[A]\{X\}=\{B\}$
	1) In LU decomposition, will first decompose the matrix $[A]$ into $[L]$ and $[U]$ matrices where: $$[A]=[L][U]$$
	- To form $[U]$, simply do forward elimination and produce an upper triangle matrix using $[A]$.
	- To form $[L]$, simply form this matrix: $$\begin{bmatrix} 1\ \quad 0 \quad 0 \cr f_{21} \quad 1 \quad 0 \cr f_{31} \quad f_{31} \quad 1 \end{bmatrix}$$
	- Then to find the $f$'s: $$f_{21}=\frac{a_{21}}{a_{11}} ,\quad f_{31}=\frac{a_{31}}{a_{11}}, \quad f_{32}=\frac{a'_{32}}{a'_{22}}$$
	- to check if $[L]$ and $[U]$ are correct, we can multiply them, we will get $[A]$ 
	2)  Then $L$ is used to generate an intermediate vector, $\{D\}$ using:$$[L]\{D\}=\{B\}$$
	3) Then $\{D\}$ is used to calculate $\{X\}$ by this equation: $$[U]\{X\}=[D]$$

### Can also use LU decomposition to find inverse of matrix
- We can also compute $A^{-1}$ using LU decomposition, ultimately, we know that $I=\begin{bmatrix} 1 \space 0 \space 0 \cr 0 \space 1 \space 0 \cr 0 \space 0 \space 1 \end{bmatrix}$, which means that the all columns of the identity matrix are such that:$$[A]\begin{bmatrix} b_{11} \cr b_{21} \cr b_{31} \end{bmatrix}=\begin{bmatrix} 1 \cr 0 \cr 0 \end{bmatrix}, [A]\begin{bmatrix} b_{12} \cr b_{22} \cr b_{32} \end{bmatrix}=\begin{bmatrix} 0 \cr 1 \cr 0 \end{bmatrix}, [A]\begin{bmatrix} b_{13} \cr b_{23} \cr b_{33} \end{bmatrix}=\begin{bmatrix} 0 \cr 0 \cr 1 \end{bmatrix}$$ 
- where $b_{ij}$ are the elements of $A^{-1}$
- then we will solve each of them normally as explained in the above part by LU decomposition, to find the corresponding columns of the inverse matrix $A^{-1}$ 

## Iterative methods:

### Gauss-Seidel Method:
most commonly used iterative method to linear algebraic equations
- uses successive substitution
- after solving the equations, we will get approximate results for all x's then to make the x's more accurate/minimize the error, we can use the new values again for the initial guesses, and substitute.
- start with an initial guess, if we don't know an initial guess, we can pick any arbitrary x
- steps for example of 3 equations:
steps:
1) we will start by finding $x_1$ by taking the initial guesses for $x_2$ and $x_3$ as 0
2) then with the found value of $x_1$, we used it to find $x_2$ but still keeping $x_3$ as 0
3) then find $x_3$ with the approximate values of $x_1$ and $x_2$
4) we will continue like this for all x's
5) to minimize the error, we can use the approximate values of $x$'s we just found until we reach a satisfiable value of error

- may not converge if not diagonally dominant: Not all systems of equations converge using Gauss-Seidel, to solve this problem, we have to make the system of equations (matrix) diagonally dominant, meaning the diagonal values should be greater than the values before them in the rows

side note: gauss-seidel is more efficient than Jacobian method

