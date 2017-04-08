***IN DEVELOPMENT***

# Matplotlib

This serves as a cheat sheet for Matplotlib, a 2d plotting library for Python.

Not a total beginner? Jump straight down to the [examples](#examples) or get the [jupyter notebook file](https://github.com/juliangaal/python-cheat-sheet/blob/master/Matplotlib/examples.ipynb). Also, the official [example library](http://matplotlib.org/examples/index.html) is pretty sweet.

If you don't already have it **installed**:
```
$ pip install matplotlib
```
or
```
$ conda install matplotlib
```
Or check out the official [installation guide](http://matplotlib.org/users/installing.html).

## Index
1. [Prepare Data](#prepare)
2. [Plots](#plots)
    * [Creating Plots](#plots)
        * [Figure](#figure)
        * [Axes](#axes)
    * [Plotting](#plotting)
        * [1D Data](#1d)
        * [2D Data](#2d)
        * [Saving Plots](#save)
    * [Customization](#custom)
        * [Colors](#colors)
        * [Markers](#markers)
        * [Lines](#lines)
        * [Text](#text)
        * [Limits, Labels, Layout](#limits)
3. [Examples](#examples)
    * [Basics](#basics)
    * [Subplotting](#sub)
    * [Advanced](#advanced)

## 1. Prepare Data <a name="prepare"></a>

NumPy ([my cheat sheet](https://github.com/juliangaal/python-cheat-sheet/blob/master/NumPy/NumPy.md), [official docs](http://www.numpy.org/)) or [Pandas](http://pandas.pydata.org/) is probably your best friend for that.

## 2. Plots <a name="plots"></a>

### Creating plots

*Figure* <a name="figure"></a>

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
| `fig = plt.figure()`      | a container that contains all plot elements | [link](http://matplotlib.org/api/figure_api.html) |

*Axes* <a name="axes"></a>

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
| `fig.add_axes()`<br/>`a = fig.add_subplot(222)` |Initializes subplot <br/> A subplot is an axes on a grid system <br/> row-col-num, see [examples](#examples) | [link](http://matplotlib.org/api/figure_api.html#matplotlib.figure.Figure.add_axes) <br/> [link](http://matplotlib.org/api/figure_api.html#matplotlib.figure.Figure)|
| `fig, b = plt.subplots(nrows=3, nclos=2)`|Adds subplot| [link](http://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.subplot)|
|`ax = plt.subplots(2, 2)`|Creates subplot|[link](http://matplotlib.org/api/pyplot_api.html?highlight=subplots#matplotlib.pyplot.subplots)|

Axes are very useful for subplots. See example [here](#axes)

**After configuring your plot, you must use `plt.show()` to make it visible**

### Plotting <a name="1d"></a>

*1D Data* <a name="plotting"></a>

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
| `lines = plt.plot(x,y)`|Plot data connected by lines|[link](http://matplotlib.org/api/pyplot_api.html?highlight=plot#matplotlib.pyplot.plot)|
| `plt.scatter(x,y)`|Creates a scatterplot, unconnected data points|[link](http://matplotlib.org/api/_as_gen/matplotlib.axes.Axes.scatter.html?highlight=scatter#matplotlib.axes.Axes.scatter)|
| `plt.bar(xvalue, data , width, color...)`|simple vertical bar chart|[link](http://matplotlib.org/api/pyplot_api.html?highlight=bar#matplotlib.pyplot.bar)|
| `plt.barh(yvalue, data, width, color...)`|simple horizontal bar|[link](http://matplotlib.org/api/pyplot_api.html?highlight=barh#matplotlib.pyplot.barh)|
|`plt.hist(x, y)`|Plots a histogram|[link](http://matplotlib.org/api/pyplot_api.html?highlight=hist#matplotlib.pyplot.hist)|
|`plt.boxplot(x,y)`|Box and Whisker plot|       |[link](http://matplotlib.org/api/pyplot_api.html?highlight=boxplot#matplotlib.pyplot.boxplot)|
|`plt.violinplot(x, y)`| Creates violin plot       |[link](http://matplotlib.org/api/pyplot_api.html?highlight=violinplot#matplotlib.pyplot.violinplot)|
|`ax.fill(x, y, color='lightblue')`<br/>`ax.fill_between(x,y,color='yellow')`|Fill area under/between plots|[link](http://matplotlib.org/api/pyplot_api.html?highlight=fill#matplotlib.pyplot.fill)|

For more advanced box plots, start [here](http://matplotlib.org/api/pyplot_api.html?highlight=bar#matplotlib.pyplot.boxplot)

*2D Data* <a name="2d"></a>

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
|`fig, ax = plt.subplots()`</br>`im = ax.imshow(img, cmap, vmin...)`|Colormapped or RGB arrays| [link](http://matplotlib.org/api/_as_gen/matplotlib.axes.Axes.imshow.html?highlight=imshow#matplotlib.axes.Axes.imshow)|

Suggestions?

*Saving plots* <a name="save"></a>

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
|`plt.savefig('pic.png')`|Saves plot/figure to image|[link](http://matplotlib.org/api/pyplot_api.html?highlight=savefig#matplotlib.pyplot.savefig)|
|`plt.savefig('transparentback.png', transparent=True)`|Saves transparent plot/figure to image|see above|


### Customization <a name="custom"></a>

*Color* <a name="colors"></a>

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
| `plt.plot(x, y, color='lightblue')`<br/>`plt.plot(x, y, alpha = 0.4)`|colors plot to color blue|[link](http://matplotlib.org/api/pyplot_api.html?highlight=plot#matplotlib.pyplot.plot)|
|`plt.colorbar(mappable, orientation='horizontal')`|`mappable`: the Image, Contourset etc to which colorbar applies|[link](http://matplotlib.org/api/pyplot_api.html?highlight=colorbar#matplotlib.pyplot.colorbar)|

*Markers* <a name="markers"></a> (see [examples](#examples))

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
| `plt.plot(x, y, marker='*')`|adds `*` for every data point|[link](http://matplotlib.org/api/markers_api.html?highlight=marker#module-matplotlib.markers)|
| `plt.scatter(x, y, marker='.')` |adds . for every data point|see above|

*Lines* <a name="lines"></a>

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
|`plt.plot(x, y, linewidth=2)`|Sets line width|[link](http://matplotlib.org/api/pyplot_api.html?highlight=plot#matplotlib.pyplot.plot)|
|`plt.plot(x, y, ls='solid')`|Sets linestyle, `ls` can be ommitted, see 2 below|see above|
|`plt.plot(x, y, ls='--')`|Sets linestyle, `ls` can be ommitted, see below|see above|
|`plt.plot(x,y,'--', x**2, y**2, '-.')`|Lines are '--' and '_.', see [example](#crazylines)|see above|
|`plt.setp(lines,color='red',linewidth=2)`|Sets properties of plot `lines`|[link](http://matplotlib.org/api/pyplot_api.html?highlight=setp#matplotlib.pyplot.setp)|

*Text* <a name="text"></a>

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
|`plt.text(1, 1,'Example Text',style='italic')`|Places text at coordinates 1/1|[link](http://matplotlib.org/api/pyplot_api.html?highlight=text#matplotlib.pyplot.text)|
|`ax.annotate('some annotation', xy=(10, 10))`|Annotate the point with coordinates`xy` with text `s`|[link](http://matplotlib.org/api/pyplot_api.html?highlight=annotate#matplotlib.pyplot.annotate)|
|`plt.title(r'$delta_i=20$', fontsize=10)`|Mathtext|[link](http://matplotlib.org/users/mathtext.html)|

*Limits, Legends/Labels , Layout* <a name="lll"></a>

*Limits*

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
|`plt.xlim(0, 7)`|Sets x-axis to display 0 - 7 |[link](http://matplotlib.org/api/pyplot_api.html?highlight=xlim#matplotlib.pyplot.xlim)|
|`plt.ylim(-0.5, 9)`|Sets y-axis to display -0.5 - 9|[link](http://matplotlib.org/api/pyplot_api.html?highlight=ylim#matplotlib.pyplot.ylim)|
|`ax.set(xlim=[0, 7], ylim=[-0.5, 9])`<br/>`ax.set_xlim(0, 7)`|Sets limits|[link]()<br/>[link](http://matplotlib.org/api/_as_gen/matplotlib.axes.Axes.set_ylim.html?highlight=ylim#matplotlib.axes.Axes.set_ylim)|
|`plt.margins(x=1.0, y=1.0)`|Set margins: add padding to a plot, values 0 - 1||
|`plt.axis('equal')`|Set the aspect ratio of the plot to 1||

*Legends/Labels*

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
|`plt.title('just a title')`|Sets title of plot|[link](http://matplotlib.org/api/pyplot_api.html?highlight=title#matplotlib.pyplot.title)|
|`plt.xlabel('x-axis')`|Sets label next to x-axis|[link](http://matplotlib.org/api/pyplot_api.html?highlight=xlabel#matplotlib.pyplot.xlabel)|
|`plt.ylabel('y-axis')`|Sets label next to y-axis|[link](http://matplotlib.org/api/pyplot_api.html?highlight=ylabel#matplotlib.pyplot.ylabel)|
|`ax.set(title='axis', ylabel='Y-Axis', xlabel='X-Axis')`|Set title and axis labels|[link](http://matplotlib.org/api/_as_gen/matplotlib.axes.Axes.set.html?highlight=set#matplotlib.axes.Axes.set)|
|`ax.legend(loc='best')`|No overlapping plot elements|[link](http://matplotlib.org/api/_as_gen/matplotlib.axes.Axes.legend.html?highlight=legend#matplotlib.axes.Axes.legend)|

*Ticks*

| Operator    | Description     | Documentation |
| :------------- | :------------- | :----------- |
|`plt.xticks(x, labels, rotation='vertical')`|Set ticks, [example](#ticks)|[link](http://matplotlib.org/examples/ticks_and_spines/ticklabels_demo_rotation.html)|
|`ax.xaxis.set(ticks=range(1,5), ticklabels=[3,100,-12,"foo"])`|Set x-ticks|[link](http://matplotlib.org/api/_as_gen/matplotlib.axis.XAxis.set.html?highlight=xaxis%20set#matplotlib.axis.XAxis.set)|
|`ax.tick_params(axis='y', direction='inout', length=10)`|Make y-ticks longer and go in and out|[link](http://matplotlib.org/api/_as_gen/matplotlib.axes.Axes.tick_params.html?highlight=tick_params#matplotlib.axes.Axes.tick_params)|

## Examples <a name="examples"></a>

### Basics <a name="basics"></a>
```python
import matplotlib.pyplot as plt

x = [1, 2.1, 0.4, 8.9, 7.1, 0.1, 3, 5.1, 6.1, 3.4, 2.9, 9]
y = [1, 3.4, 0.7, 1.3, 9, 0.4, 4, 1.9, 9, 0.3, 4.0, 2.9]
plt.scatter(x,y, color='red')

w = [0.1, 0.2, 0.4, 0.8, 1.6, 2.1, 2.5, 4, 6.5, 8, 10]
z = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
plt.plot(z, w, color='lightblue', linewidth=2)

c = [0,1,2,3,4, 5, 6, 7, 8, 9, 10]
plt.plot(c)

plt.ylabel('some numbers')
plt.xlabel('some more numbers')
plt.show()
```
![alt-text](/img/plot.png)

<a name="crazylines"></a>
```python
import matplotlib.pyplot as plt
import numpy as np

x = np.random.rand(10)
y = np.random.rand(10)

plt.plot(x,y,'--', x**2, y**2,'-.')
plt.savefig('lines.png')
plt.show()
```
![alt-text](/img/lines.png)

<a name="ticks"></a>
```python
import matplotlib.pyplot as plt


x = [1, 2, 3, 4]
y = [1, 4, 9, 6]
labels = ['Frogs', 'Hogs', 'Bogs', 'Slogs']

plt.plot(x, y, 'ro')
# You can specify a rotation for the tick labels in degrees or with keywords.
plt.xticks(x, labels, rotation='vertical')
# Pad margins so that markers don't get clipped by the axes
plt.margins(0.2)
plt.savefig('ticks.png')
plt.show()
```
![alt-text](/img/ticks.png)

### Subplotting Examples <a name="sub"></a>
```python
import matplotlib.pyplot as plt

x = [0.5, 0.6, 0.8, 1.2, 2.0, 3.0]
y = [10, 15, 20, 25, 30, 35]
z = [1, 2, 3, 4]
w = [10, 20, 30, 40]

fig = plt.figure()
ax =  fig.add_subplot(111)
ax.plot(x, y, color='lightblue', linewidth=3)
ax.scatter([2,3.4,4, 5.5],
               [5,10,12, 15],
               color='black',
               marker='^')
ax.set_xlim(0, 6.5)

ax2 =  fig.add_subplot(222)
ax2.plot(z, w, color='lightgreen', linewidth=3)
ax2.scatter([3,5,7],
               [5,15,25],
               color='red',
               marker='*')
ax2.set_xlim(1, 7.5)

plt.savefig('mediumplot.png')
plt.show()
```
![alt-text](/img/medium.png)

Thanks to this guy for this [good example](http://stackoverflow.com/questions/37970424/what-is-the-difference-between-drawing-plots-using-plot-axes-or-figure-in-matpl) <a name="axes"></a>
```python
import numpy as np
import matplotlib.pyplot as plt

# First way #

x = np.random.rand(10)
y = np.random.rand(10)

figure1 = plt.plot(x,y)

# Second way #

x1 = np.random.rand(10)
x2 = np.random.rand(10)
x3 = np.random.rand(10)
x4 = np.random.rand(10)
y1 = np.random.rand(10)
y2 = np.random.rand(10)
y3 = np.random.rand(10)
y4 = np.random.rand(10)

figure2, ((ax1, ax2), (ax3, ax4)) = plt.subplots(2, 2)
ax1.plot(x1,y1)
ax2.plot(x2,y2)
ax3.plot(x3,y3)
ax4.plot(x4,y4)

plt.show()
```
If you haven't used NumPy before, check out my [cheat sheet](https://github.com/juliangaal/python-cheat-sheet/blob/master/NumPy/NumPy.md)

![alt-text](/img/axes.png)

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(0, 1, 500)
y = np.sin(4 * np.pi * x) * np.exp(-5 * x)

fig, ax = plt.subplots()

ax.fill(x, y, color='lightblue')
plt.show()
```
![alt-text](/img/fill.png)

[source](http://matplotlib.org/api/pyplot_api.html?highlight=fill#matplotlib.pyplot.fill)

### Advanced <a name="advanced"></a>

Taken from [official docs](http://matplotlib.org/api/pyplot_api.html)
```python
import matplotlib.pyplot as plt
import numpy as np


np.random.seed(0)

x, y = np.random.randn(2, 100)
fig = plt.figure()
ax1 = fig.add_subplot(211)
ax1.xcorr(x, y, usevlines=True, maxlags=50, normed=True, lw=2)
ax1.grid(True)
ax1.axhline(0, color='black', lw=2)

ax2 = fig.add_subplot(212, sharex=ax1)
ax2.acorr(x, usevlines=True, normed=True, maxlags=50, lw=2)
ax2.grid(True)
ax2.axhline(0, color='black', lw=2)

plt.show()
```
![alt-text](/img/advanced.png)

Sources: [Datacamp](www.datacamp.com), [Official Docs](http://matplotlib.org/api/) and [Quandl](https://s3.amazonaws.com/quandl-static-content/Documents/Quandl+-+Pandas,+SciPy,+NumPy+Cheat+Sheet.pdf)
