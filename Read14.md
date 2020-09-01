__Read: Class 14__

# Readings: Data Visualization [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read14.md)

## Matplotlib tutorial:
  - matplotlib is probably the single most used Python package for 2D-graphics. 
  - It provides both a very quick way to visualize data from Python and publication-quality figures in many formats.
- __IPython and the pylab mode__:
  - IPython is an enhanced interactive Python shell that has lots of interesting features including named inputs and outputs, access to shell commands, improved debugging and much more.
  - When we start it with the command line argument -pylab (--pylab since IPython version 0.12), it allows interactive matplotlib sessions that have Matlab/Mathematica-like functionality.
- __pyplot__:
  - pyplot provides a convenient interface to the matplotlib object-oriented plotting library.
  - It is modeled closely after Matlab(TM). Therefore, the majority of plotting commands in pyplot have Matlab(TM) analogs with similar arguments. 
  - Important commands are explained with interactive examples.
- __Simple plot__:
  - Changing colors and line widths:  [Line API](https://matplotlib.org/api/artist_api.html#matplotlib.lines.Line2D) -  [Controlling line properties](https://matplotlib.org/tutorials/introductory/pyplot.html)
  - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/exercice_3.png)
  - <pre>plt.figure(figsize=(10,6), dpi=80)</pre>
  - <pre>plt.plot(X, C, color="blue", linewidth=2.5, linestyle="-")</pre>
  - <pre> plt.plot(X, S, color="red",  linewidth=2.5, linestyle="-")</pre>
- __Setting limits__:  [xlim() command](https://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.xlim) - [ylim() command](https://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.ylim)
  - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/exercice_4.png)
  - <pre> plt.xlim(X.min()*1.1, X.max()*1.1)</pre>
  - <pre> plt.ylim(C.min()*1.1, C.max()*1.1)</pre>
- __Setting ticks__: [xticks() command](https://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.xticks) - [yticks() command](https://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.yticks) - [Tick container
](https://matplotlib.org/users/artists.html#axis-container)  - [Tick locating and formatting](https://matplotlib.org/api/ticker_api.html)
  - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/exercice_5.png)
  - <pre>plt.xticks( [-np.pi, -np.pi/2, 0, np.pi/2, np.pi])</pre>
  - <pre>plt.yticks([-1, 0, +1])</pre>
- __Figures, Subplots, Axes and Ticks__:
  - Figures:A figure is the windows in the GUI that has "Figure #" as title. Figures are numbered starting from 1 as opposed to the normal Python way starting from 0. 
  
|Argument	  |Default	        |Description                                |
|  ---      | ---             | ---                                       |
|num	      |1	              |number of figure                           |
|figsize	  |figure.figsize	  |figure size in in inches (width, height)   |
|dpi	      |figure.dpi	      |resolution in dots per inch                |
|facecolor	|figure.facecolor	|color of the drawing background            |
|edgecolor	|figure.edgecolor	|color of edge around the drawing background|
|frameon	  |True           	|draw figure frame or not                   |

- __Animation__: [Animation](https://matplotlib.org/api/animation_api.html)
  - __Drip drop__:
  - convert this img from this:
  - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/rain-static.png)
  
  - first use this snippet code :
  <code># New figure with white background
  fig = plt.figure(figsize=(6,6), facecolor='white')

  # New axis over the whole figure, no frame and a 1:1 aspect ratio
  ax = fig.add_axes([0,0,1,1], frameon=False, aspect=1)</code>
  - then using this snippet code:
  - <code>
  # Number of ring
  n = 50
  size_min = 50
  size_max = 50*50

  # Ring position
  P = np.random.uniform(0,1,(n,2))

  # Ring colors
  C = np.ones((n,4)) * (0,0,0,1)
  # Alpha color channel goes from 0 (transparent) to 1 (opaque)
  C[:,3] = np.linspace(0,1,n)

  # Ring sizes
  S = np.linspace(size_min, size_max, n)

  # Scatter plot
  scat = ax.scatter(P[:,0], P[:,1], s=S, lw = 0.5,
                  edgecolors = C, facecolors='None')

  # Ensure limits are [0,1] and remove ticks
  ax.set_xlim(0,1), ax.set_xticks([])
  ax.set_ylim(0,1), ax.set_yticks([])
  </code>
  - converted to this: 
  - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/rain.gif)

- __Other Types of Plots__:
  - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/plot.png)
    - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/scatter.png)
      - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/bar.png)
        - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/contour.png)
          - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/imshow.png)
            - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/quiver.png)
              - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/pie.png)
                - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/grid.png)
                - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/multiplot.png)
                - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/polar.png)
                - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/plot3d.png)
                - ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/text.png)
                -  ![img](https://github.com/rougier/matplotlib-tutorial/raw/master/figures/plot_ex.png)
                
                
  ---
  [Python Data Science cheat Sheet](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Python_Seaborn_Cheat_Sheet.pdf)
