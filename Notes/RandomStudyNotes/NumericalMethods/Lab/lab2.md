#### More about plotting graphs:
- To change the attributes `color`, `shape`, and `line style`, we will add one more argument to `plot(x,y)`, to see all the options, just do `help plot`:
```
plot(x, y, 'sr-')
```

- To change `Linewidth`, `Markersize`, `MarkerEdgeColor`, `MarkerFaceColor`, will add, again we can just use `help plot` to copy/paste this code:
```
plot(x,y,'--rs','LineWidth',2,...  
	'MarkerEdgeColor','k',...  
	'MarkerFaceColor','g',...  
	'MarkerSize',10)
```

- To make multiple plots in one graph, can be used for plotting different quantity graphs:
```
subplot(m, n, p)
```
- where: m is number of rows, n is number of columns, p is the window that will be activated.
- ==Try this at home== 