- When there is only one independent variable, then we call the equation as Ordinary Differential Equation (ODE)
- If there is more than one independent variable then we call it partial differential equation
- For example in, $$\frac{dv}{dt}=g-\frac{c}{m}v$$
- The only one independent variable is $dt$ so it is an ordinary differential equation
- Note when we have "initial conditions", then that means that we will be given values that are to be input in the first step of the iterations.
- Problems with "temporal conditions" mean that it is asking about time.

- We will do:
	- Runge-Kutta first order methods
		1) Euler's method
		2) Heun's method
		3) Midpoint method
	- Runge-Kutta second order methods
		1) Heun's method
		2) MIdpoint method
		3) Ralston's method (a)
	- Runge-Kutta fourth order methods
		- Classical fourth order RK method
	- Higher order differential equations

## One-step Methods: 1st order Runge-Kutta methods
- Basically we want to extrapolate or approximate a $y$ value given the ODE of the original function and initial conditions.
- We have the general form: $$y_{i+1}=y_i+ \phi h$$
- Similarly, we can also say: $$new\ value=old\ value + slope\times step\ size $$
- All one-step methods are of this form with the exception that $\phi$ is different in those methods.
### Euler Method
- It is just the first order Taylor series method: 
- Problem is that we want to approximate a $y$ value without being given the original function, but we will be given the derivative of that function: $\frac{dy}{dx}=f(x,y)$ (the ODE), he initial condition, and $h$
- Here, $\phi$ will be: $\frac{dy}{dx}=f(x,y)$: $$y_{i+1}=y_i + f(x,y)h$$
- Reducing step size will reduce the error, but there will be no error if it is a linear equation
- Euler’s method error is due mainly to global truncation errors 
- (global=local truncation + propagation of truncation error)

### Heun's method: Improving Euler's method
- We will take 2 derivatives, one at initial point $(x_i,y_i)$, and at the end point $(x_{i+1}, y_{i+1})$ 
- Then take the average of both derivatives and will obtain an improved approximation
- here, for the equation $$y_{i+1}=y_i+ \phi h$$
- where $\phi$ will be: $$\frac{f(x_i,y_i) + f(x_{i+1}, y_{i+1}) }{2} $$
- note: $f(x, y )$ is the derivative

### The Midpoint (Improved Polygon) Method
- Uses Euler's method to predict a value of $y$ by using the gradient at the midpoint of the interval
- here, for the equation $$y_{i+1}=y_i+ \phi h$$
- where $\phi$ will be: $$f(x_{i+1/2}, y_{i+1/2} )$$
- note: here $\phi$ is the gradient of the midpoint of the interval instead of the 

## Runge-Kutta methods for higher order
- More accurate than Taylor series approach without calculating higher derivatives
- We have the general form: $$y_{i+1}=y_i+ \phi(x_i, y_i, h)h$$
- Where $\phi(x_i, y_i, h)$ is called the increment function and it is a linear equation, and different methods have different $\phi$  

### Runge-Kutta methods: Second Order
- For second order RK methods, the increment function $\phi(x_i, y_i, h)$ will be: $$y_{i+1}=y_i+(a_1k_1+a_2k_2)h$$
- where
	- $k_1=f(x_i, y_i)$
	- $k_2=f(x_i+ p_1h, \ y_i+q_{11}k_1h)$ 

- and the unknowns here can be directly written with the equations for $a_1$, $p_1$ and $q_{11}$: 
	- $a_1=1-a_2$,
	- $p_1=q_{11}=\frac{1}{2a_2}$

- **Here, choosing the value for $a_2$ determines the Runge-Kutta method to be used, we will study about 3 values for $a_2$**

#### 1) When $a_2=1/2$, Huen's method
- Equation will be: $$y_{i+1}=y_i+(\frac{1}{2}k_1+\frac{1}{2}k_2)h$$
#### 2) When $a_2=1$, Midpoint method
- Equation will be: $$y_{i+1}=y_i+ k_2h$$
#### 3) When $a_2=2/3$, Ralston's method
- Equation will be: $$y_{i+1}=y_i+(\frac{1}{3}k_1+\frac{2}{3}k_2)h$$

### Runge-Kutta methods: fourth Order
- most widely used
- One form is most commonly used, also called classical fourth order RK method $$y_{i+1} = y_i + \frac{1}{6} (k_1 + 2k_2 + 2k_3 + k_4)h$$
- Where $k_1$ etc. are equal to ==need to complete== 


### Application of differential equations: Predator-Prey Model: Lotka-Volterra equations: not coming in exam

## Higher-Order ODE

- Will convert the higher order differential equations to 1st order differential equation, then make a system of linear equations and solve them, e.g. will convert all the $\ddot{z}$  etc. to be $\dot{z}$ (i.e. first order ODE) 
- Will end up with a matrices of system of equations, and the initial conditions (and the step size if using Euler's methods etc.)
