## Why Numerical Methods?
-  many problems in engineering do not have exact solutions so we need numerical methods
- Used to Solve problems approximately
- We can simulate natural processes using numerical methods, so we do not always need to experiment many times, and just prepare the solution using the simulation
- Numerical methods are algorithm used to obtain approximate numerical solution of a mathematical problem.
## Accuracy & Precision
- **Accuracy** refers to one measured value, it sees how close an approximation is to a correct answer, there are two ways to define accuracy:
	1) absolute error
	2) relative error
- **Precision  (repeatability)** refers to multiple measured values, and measurements are precise if they are close to each other, not necessarily close to the true value.
- **Inaccuracy (or bias)** : A systematic deviation from the actual value
- **Imprecision (or uncertainty)** : Magnitude of scatter.
- We can easily adjust/fix highly precise but not accurate solutions by just "moving" them over/translating them closer to the actual value, for example, if we measure something using a ruler and it has a zero error, then we can do $\pm The \space error \space value$ 
## Error
- $Error=Exact\space Value - Approximate \space Value$ or also called *absolute error*
- $True\space Relative\space Error\space (\epsilon_t)=\frac{ExactVal-ApproximateVal}{ExactVal}\times100$ , we can use this to check if experiment lies within this, then we will accept the experiment.
## Iteration method:
- **But** since there is no exact solution if we cannot solve problem analytically, then we will use percent relative error $\epsilon_a$, $$\epsilon_a=\frac{currentApproximation- previousApproximation}{currentApproximation}\times100$$
> Numerical methods use iterative approach to compute answers, A present approximation is made based on a previous approximation.

- We move to the next step only when error between the previous step and current step is within the tolerance range.
- The less the tolerance, the more the iterations
- Then we stop when we reach a stopping criterion called *percent tolerance* $\epsilon_s$ (we stop the iterations).$$|\epsilon_a| < |\epsilon_s|$$

- to find error of approximate measurement, then we will do similar to analytical solution (exact), but here we do not know the exact value, so we will do the previous measurement minus the next measurement
- It is also called iterative Process, as we keep subtracting the previous measurement from $f(x_i) - f(_{x+1}) < \epsilon_S$ 

## Finding Approximation
- We can find the *percent tolerance*, for $n$ number of significant figures using the following formula: $$\epsilon_s=(0.5\times10^{2-n})$$
- For example, if I want a *percent tolerance* for a solution for 3 sig figs, then: $$\epsilon_s=(0.5\times10^{2-n}) = 0.05\%$$

## Types of Errors
- Round-Off errors
- Truncation errors: used in approximations

## Approximating using Taylor Series
- The higher the order of approximation applied, the lower the truncation error
- if we are doing for example, second order approximation, then we will take upto the second derivative
- Since Taylor approximation is *just* an approximation to the true value of $f(x)$, so there is always a remainder or the *difference between the true value and the approximation*, and that is $R_n$. The lower the remainder, the more accurate the solution
- Remainder term, $R_n$ : $$R_n= \frac{f^{n+1}(\zeta)}{(n+1)!}(x_{i+1}-x_i)^{n+1}$$
- $\zeta$ is not know exactly, it lies somewhere between the range $h$ or we can say $R=O(h^{n+1})$ , the order of truncation error is $n+1$ 

- To approximate a function using Taylor series, then, we have the given: 
	- $f(x)$ the function to approximate
	- $x_{i+1}$ the point to approximate
	- $x_i$ the reference point
