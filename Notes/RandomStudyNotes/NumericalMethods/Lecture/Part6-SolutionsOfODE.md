- When there is only one independent variable, then we call the equation as Ordinary Differential Equation (ODE)
- If there is more than one independent variable then we call it partial differential equation
- For example in, $$\frac{dv}{dt}=g-\frac{c}{m}v$$
- The only one independent variable is $dt$ so it is an ordinary differential equation
- Note when we have "initial conditions", then that means that problem involves time, also called temporal conditions

## Taylor Series Method
- 

## One-step Methods
- We have the general form: $$y_{i+1}=y_i+ \phi h$$
- All one-step methods are of this form with the exception that $\phi$ is different in those methods
### Euler Method
- It is just the first order Taylor series method: 
- reducing step size will reduce the error, but there will be no error if it is a linear equation
- Here, $\phi$ will be:

### Heun's method
- We will take 2 derivatives, one at initial point, and at the end point
- Then take the average of both derivatives and will obtain an improved approximation

### The Midpoint (Improved Polygon) Method
- Same as Euler method but will take extra point 

## Runge-Kutta methods
- More accurate than taylor series approach without calculating higher derivatives
- We have the general form: $$y_{i+1}=y_i+ \phi(x_i, y_i, h)h$$
- Where $\phi(x_i, y_i, h)$ is called the increment function and it is a linear equation, and the different methods will have this different

### Runge-Kutta methods: Second Order
- For second order RK methods, $\phi(x_i, y_i, h)$ can be directly written with 2 equation for $a_1$ and $p_1$ while already assuming $a_2$, and we will substitute these in the following methods to obtain the answer.
==need to complete==

### Runge-Kutta methods: fourth Order
- most accurate
- Will do iterations by finding new y from the previous y

### Predator-Prey Model: Lotka-Volterra equations: not coming in exam

## Higher-Order ODE

- Need to convert it into 1st order differential equation
- Will do this using substituting order of differential equations to z, 
- and will solve using any method