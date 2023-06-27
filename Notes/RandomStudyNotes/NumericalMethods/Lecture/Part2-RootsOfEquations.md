## Non-linear Equation Solvers:

- There are two methods:
	1) Bracketing: 
		- Graphical
		- Bisection
		- False Position
	1) Open Methods: 
		- Simple fixed-point iteration
		- Newton-Raphson
		- Secant method
		- Multiple roots

- Some problems do not have proper solutions to find roots of equations, so we will use the two aforementioned methods
## Bracketing

- We will do bracketing around where function is positive and negative, and keep closing in the brackets, until 
- How to find the intervals/range/place where the roots and the brackets should be: we will do incremental search, In this we will first take a wide bracket then start closing it.
### Bisection Method:
- Bisection method (interval halving): We will repeatedly half the intervals until we reach the root:
	- pick $f(x_l)$ and $f(x_u)$ (f(x) lower and f(x) upper)
	- divide the range by 2 and we will get $f(x_r)$ i.e. $$x_r=\frac{x_l+x_u}{2}$$
	- take $f(x_l)$ and multiply it with $f(x_u)$ and if $f(x_l)\times f(x_u)<0$   then root lies in lower subinterval and vice versa
	- ==NEED to write the rest of the method for doing Bisection method==
	- Will stop when we reach below a certain error i.e. $\epsilon_a < \epsilon_s$ 

### False-position Method:
shortcoming of bisection is that we divide in equal halves everytime, so it might take a lot of iterations
- to tackle this and lessen the number of our iterations, we can imagine an imaginary line between $x_l$ and $x_u$ and we can say that the intersection point of this imaginary line is very close to the actual root
steps:
- first take 
- then make an estimate for the root that will be equal to $x_r$
- then do $f(x_l)\times f(x_u)<0$, and if negative, then update $x_u$ to $x_r$
- and 
But false-position may also sometimes perform poorly, in case when the range ($x_l$ and $x_u$) are chose such that the actual root is far away from the intersection of the imaginary line (slide 22).

## Open Methods
- Bracketing methods always converge towards the solution.
- Open methods are based on formulas that require only a single starting value of x or 2 starting values that do not necessarily bracket the root.
- These methods sometimes diverge form the root as the computation progresses.
- however when they converge they converge very quickly comparted to the bracketing methods, so have even less number of iterations.

### Simple fixed-point iteration
- First make the original function $f(x) = 0$
- and then will rearrange the equation $f(x)$ such that $x=g(x)$, meaning will keep only one $x$ at the left-hand side of the equation.
- Then will use g(x) to predict the new value of x, that is $x_{i+1} = g(x_i)$ 
- will need to see if converging every time before continuing
- ==need to see how to actually do it==

### Newton-Raphson Method
 - take the derivative (linearize it) 
 - ==need to see how to actually do it==

### Secant Method
- Sometimes derivatives make it difficult to solve using N-R method in complicated functions, but since we do not take the derivative here, there will be more error in secant method.
- These derivatives can be approximated using a finite divided difference
- finite divided difference: Given any domain, divide it into many sections such that we can approximate each point,  
steps:
- will be given initial guesses as $x_{-1}$ or $x_0$
- ==need to see how to actually do it==

### Multiple roots
- to find multiple roots, we can use a modified Newton-Raphson method
- ==see how to do it==
