### Differentiating normally:
- `syms x` will tell matlab to differentiate on x
- then to differentiate, write:
```
syms x;
diff(function, order of differentiating like, 2, 3 etc.)
```

- to differentiate for 2 variables:
```
syms x t;
diff(sin(x*t^2), x)
% will differentiate with respect to x here
diff(sin(x*t^2), t)
% will differentiate with respect to t here
```

- to find dy/dx values from x=0 to 0.8, using anonymous function:
```
f = @(x) 0.2 + 25*x - 200*x.^2
x = 0 : 0.1 : 0.8;
y = f(x); % doing this to make the y values vector
d = diff(y)./diff(x) % take care to add the dot
```

- using `gradient` to differentiate:
```
% do same steps as above uptil differentiation func
f = @(x) 0.2 + 25*x - 200*x.^2
x = 0 : 0.1 : 0.8;
y = f(x); % doing this to make the y values vector
D = gradient(y, 0.1);
% in the second argument above, will use the same step, as defined in x
```

### Partial differential equations:
- Partial differential equations will always have 2 or more variables, will usually find the z variable which is the elevation against the x and y variables.
- first will have anonymous function with two unknown variables
```
f = @(x, y) y-x- 2*x.^2
```
- then we will add values to x and y using `meshgrid`:
```
[x, y] = meshgrid(-2:0.25:2, 1:0.25:3);
```
- then declare z:
```
z = f(x,y);
```
- then calculate WHAT
```
[fx, fy] = gradient(z, 0.25);
```
- contour is a plot, that takes the z value as height:
```
cs = contour(x, y, z);
clabel(cs); % this command will give the amount of elevation on the plot
```

### Ordinary Differential Equations (ODE)
- we only need `ode45`, which has the most applications in real life
```
[t, y] = ode45(dydt, tspan, y0)
```
- we will always get 2 outputs: t which is the time, y which is the 
- `dydt` is anonymous function with 2 unknown variables, `t` and `y`
- `tspan` is the timespan, and give it a vector without a comma between the values i.e. `tspan = [0 1]`
- `y0` is the initial value for y when time is 0.
- Note: in the end, we will display t and y like this: `[t, y]`
- and to find the values for dy/dt, we put `f` equals to the original equation, and use the calculated values of `t` and `y` to calculate values for `f`.

### System Of Equations With 2 Unknowns:
- Matlab has a neat trick on writing an anonymous function with 2 or more unknowns (system of equations):
```
dydt = @(t, y) [1.2*y(1)-0.6*y(1)*y(2) ; -0.8*y(2) + 0.3*y(1)*y(2)];
```
- so in this equation the different y's were declared in this notation: `y(1)` and `y(2)`
- then solve it using `ode45` as above, and display it like this: `[t, y]` where in this example, y will have 2 columns
==WILL FINISH LABS HERE==
