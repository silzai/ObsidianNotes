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
- We will do bracketing around where function is positive and negative, and keep closing in the brackets, until we reach the root i.e. $f(x_r)=0$ 
- How to find the intervals/range/place where the roots and the brackets should be: we will do incremental search, In this we will first take a wide bracket then start closing it.
### Bisection Method:
- Bisection method (interval halving): We will repeatedly half the intervals until we reach the root:
- steps:
	1)  pick any $x_l$ ($x$ lower) and $x_u$ ($x$ upper) 
	2) do $f(x_l)\times f(x_u)<0$ to ***confirm if the root even exists*** between the range.
	3) divide the range by 2 and we will get $x_r$ i.e. $$x_r=\frac{x_l+x_u}{2}$$
	4) If $(f(x_l)\times f(x_r)<0)$, the root lies in the lower subinterval and we will make $x_u= x_r$, and repeat from step 3.
	5) If $(f(x_l)\times f(x_r)>0)$, the root lies in the upper subinterval and we will make $x_l = x_r$ and repeat from step 3.
	6) If $(f(x_l )\times f(x_r )=0)$ the root is $x_r$ and stop.
	8) Will also stop when we reach below a certain error i.e. $\epsilon_a < \epsilon_s$ and $\epsilon_a=\frac{current.x_r-previous.x_r}{current.x_r}\times100$  

### False-position Method:
shortcoming of bisection is that we divide in equal halves every time, so it might take a lot of iterations
- to tackle this and lessen the number of our iterations, we can imagine an imaginary line between $x_l$ and $x_u$ and we can say that the intersection point of this imaginary line is very close to the actual root
steps:
1) pick any $x_l$ ($x$ lower) and $x_u$ ($x$ upper) 
2) do $f(x_l)\times f(x_u)<0$ to ***confirm if the root even exists*** between the range.
3) then take the intersection of the imaginary line between $f(x_l)$ and $f(x_u)$ with the x-axis, that will be called $x_r$ which is the estimate of the root, where $$x_r=x_u-\frac{f(x_u)(x_l-x_u)}{f(x_l)-f(x_u)}$$
4) Repeat the steps from bisection method steps 4 to 8 exactly. we are only changing the method to find $x_r$ from halving to a more efficient method.

- But false-position may also sometimes perform poorly, in case when the range ($x_l$ and $x_u$) are chose such that the actual root is far away from the intersection of the imaginary line (slide 22).

## Open Methods
- Bracketing methods always converge towards the solution.
- Open methods are based on formulas that require only a single starting value of $x$ or 2 starting values that do not necessarily bracket the root.
- These methods sometimes diverge form the root as the computation progresses.
- however when they converge they converge very quickly compared to the bracketing methods, so have even less number of iterations.

### Simple fixed-point iteration
- The next $x$ to be used i.e. $x_{i+1}$ is found using the previous $x$ i.e. $x_{i}$ 
1) First make the original function $f(x) = 0$ i.e. have 0 on the right hand side.
2) and then will rearrange the equation $f(x)$ such that $x=g(x)$, meaning will keep only one $x$ at the left-hand side of the equation.
3) Then will use $g(x)$ to predict the next value of $x$, that is $x_{i+1} = g(x_i)$ 
4) will need to see if converging every time before continuing


### Newton-Raphson Method
- The next $x$ to be used i.e. $x_{i+1}$ is found using the previous $x$ i.e. $x_{i}$ 
- An initial guess, $x_0$ will be given.
 - It will be found using the derivative: $$x_{i+1}=x_i-\frac{f(x_i)}{f'(x_i)}$$
 - this is faster than previous method, i.e. less number of iterations to reach percentage tolerance

### Secant Method
- Sometimes derivatives make it difficult to solve using N-R method in complicated functions, but since we do not take the derivative here, there will be more error in secant method.
- These derivatives $f'(x_i)$ can be approximated by a backward finite divided difference.
- finite divided difference: Given any domain, divide it into many sections such that we can approximate each point,  
steps:
- will be given initial guesses of $x_{-1}$ or $x_0$
- So the next $x$ to be used, $x_{i+1}$ will be: $$x_{i+1}=x_i-\frac{f(x_i)(x_{i-1}-x_i)}{f(x_{i-1})-f(x_i)}$$

### Multiple roots
- to find multiple roots, we can use a modified Newton-Raphson method
- ==see how to do it==
