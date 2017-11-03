# weibcdf
Just use cumulative density data by time to fit the Weibull CDF distribution 
@author: lojp


from scipy import stats # Import the scipy.stats module
from scipy.optimize import curve_fit
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import asarray as ar,exp

ydata = [0.0041999999999999997, 0.0099869999999999994, 0.015879000000000001, 
    0.021288000000000001, 0.027421000000000001, 0.035160999999999998, 
    0.041052999999999999, 0.049036000000000003, 0.057980999999999998, 
    0.066203999999999999, 0.072849999999999998, 0.079033000000000006, 
    0.083266999999999994, 0.086085999999999996, 0.0929999999999997]

x = ar(range(1,len(ydata)+1))
y = ar(ydata)
xx = ar(range(1,37))

def weibCumDist(x, a, b):
    return 1 - np.exp(-(x / b) ** a)

popt,pcov = curve_fit(weibCumDist,x,y, bounds=(0, [5, 100]))
print(popt)

fig = plt.figure(figsize=(8,6))
plt.step(x,y,'b-',where='mid',label='data')
plt.plot(xx,weibCumDist(xx,*popt),'r--',label='fit')
plt.ylabel("Cumulative density")
plt.xlabel("TIS")
plt.title('Weibull-CDF Distribution')
plt.legend()
plt.show()
