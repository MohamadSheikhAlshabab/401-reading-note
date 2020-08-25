# Readings: Game of Greed 4 [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read09.md)

## Enriching Your Python Classes With Dunder (Magic, Special) Methods:

 -  special methods are a set of predefined methods you can use to enrich your classes. They are easy to recognize because they start and end with double underscores, for example __init__ or __str__.
 - tiresome to say under-under-method-under-under Pythonistas adopted the term “dunder methods”, a short form of “double under.”
 - These “dunders” or “special methods” in Python are also sometimes called “magic methods.”
 - Object Representation: __str__, __repr__:
   1 -  __repr__: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.

   2 - __str__: The “informal” or nicely printable string representation of an object. This is for the enduser.
   
 - Operator Overloading for Comparing Accounts: __eq__, __lt__
 - Iteration: __len__, __getitem__, __reversed__
 - Operator Overloading for Merging Accounts: __add__
 - Callable Python Objects: __call__ : object callable like a regular function by adding the __call__ dunder method. 
 - Context Manager Support and the With Statement: __enter__, __exit__
 
 
 -----
 
 ## What is probability?
  - probability seeks to answer the question, “What is the chance of an event happening?” 
  - To calculate the chance of an event happening, we also need to consider all the other events that can occur. 
  - In a coin toss the only events that can happen are:
     1 -  Flipping a heads
     2 - Flipping a tails
  -  The data and the distribution:
     - Enter the normal distribution. The normal distribution refers to a particularly important phenomenon in the realm of probability and statistics. The normal distribution looks like this:   ![img](https://i.imgur.com/3vDS2Au.png)
     - the normal distribution is its symmetry and its shape.
  - Three Sigma Rule:
    -  also known as the empirical rule or 68-95-99.7 rule, is an expression of how many of our observations fall within a certain distance of the mean.
    -  that given a normal distribution, 68% of your observations will fall between one standard deviation of the mean. 95% will fall within two, and 99.7% will fall within three.![img](https://i.imgur.com/Mt3RyE0.png)
 - Z-score :
   - is a simple calculation that answers the question, “Given a data point, how many standard deviations is it away from the mean?” The equation below is the Z-score equation. ![img](https://i.imgur.com/3TuDF4G.jpg)
   
-----------
## statistics — Mathematical statistics functions:
 - Averages and measures of central location:
 
|     function    |                     description                                | 
| --------------- | -------------------------------------------------------------  |
| mean()          | Arithmetic mean (“average”) of data.                           |
| fmean()         | Fast, floating point arithmetic mean.                          |
| geometric_mean()| Geometric mean of data.                                        |
| harmonic_mean() | Harmonic mean of data.                                         |
| median()        | Median (middle value) of data.                                 |
| median_low()    | Low median of data.                                            |
| median_high()   | High median of data.                                           |
| median_grouped()| Median, or 50th percentile, of grouped data.                   |
| mode()          | Single mode (most common value) of discrete or nominal data.   |
| multimode()     | List of modes (most common values) of discrete or nomimal data.|
| quantiles()     | Divide data into intervals with equal probability.             |

-----------
## Intro to Statistics:
 1 - statistical features.
 2 - probability distributions.
 3 - bayesian statistics.
 






