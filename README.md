# weibcdf
Just use cumulative density data by time to fit the Weibull CDF distribution 
@author: lojp


references:

1, ComputSimu's blog:
http://computsimu.blogspot.com/2013/11/weibull-analysis.html

2, Wikipedia
https://en.wikipedia.org/wiki/Weibull_distribution

As a biginner of Weibull, and my raw data is cumulative probability density data, very special for existing model, comparing to weibull_min, exponweib or ComputSimu's blog. So i write this code to fit the weibull distribution.

cumulative density= 
       [0.0041999999999999997, 0.0099869999999999994, 0.015879000000000001, 
        0.021288000000000001, 0.027421000000000001, 0.035160999999999998, 
        0.041052999999999999, 0.049036000000000003, 0.057980999999999998, 
        0.066203999999999999, 0.072849999999999998, 0.079033000000000006, 
        0.083266999999999994, 0.086085999999999996, 0.0929999999999997]

The defined function:
-----------------------------------
def weibCumDist(x, a, b):
    return 1 - np.exp(-(x / b) ** a)
-----------------------------------

The important point is how to use the curve_fit:
    popt,pcov = curve_fit(weibCumDist,x,y, bounds=(0, [5, 100]))
you need add the bounds, or we have an error...
