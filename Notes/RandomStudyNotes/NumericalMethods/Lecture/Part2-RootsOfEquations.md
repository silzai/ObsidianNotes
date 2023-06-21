## Non-linear Equation Solvers:

- There are two methods:
	1) Bracketing: 
		- Graphical
		- Bisection
		- False Position
	1) Open Methods: 
		- Simple fixed
		- Newton-Raphson
		- Secant method
		- Multiple roots

- Some problems do not have proper solutions to find roots of equations, so we will use the two aforementioned methods
## Bracketing

- We will do bracketing around where function is postive and negative, and keep closing in the brackets, until 
- How to find the intervals/range/place where the roots and the brackets should be: we will do incremental search, In this we will first take a wide bracket then start closing it.
### Bisection Method:
- Bisection method (interval halving): We will repeatedly half the intervals until we reach the root:
	- pick $f(x_l)$ and $f(x_u)$ (f(x) lower and f(x) upper)
	- divide the range by 2 and we will get $f(x_r)$ i.e. $$x_r=\frac{x_l+x_u}{2}$$
	- take fxl adn multiply it with fxu and if <0 then root lies in lower subinterval and vice versa
	- ==NEED to write the rest of the method for doing Bisection method==
	- 