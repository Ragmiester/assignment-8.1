# assignment-8.1
dataset={'Max': [39, 41, 43, 47, 49, 51, 45, 38, 37, 29, 27, 25],'Min': [21, 23, 27, 28, 32, 35, 31, 28, 21, 19, 17, 18]}
import numpy as nm
import matplotlib.pyplot as plt
from scipy import optimize
months=nm.arange(12)
days=nm.linspace(0,12,num=365)
def yearly_temps(times, avg, ampl, time_offset): return (avg + ampl * nm.cos((times + time_offset) * 2 * nm.pi / times.max()))
res_max, cov_max = optimize.curve_fit(yearly_temps, months,dataset['Max'])
res_min, cov_min = optimize.curve_fit(yearly_temps, months,dataset['Min'])
plt.figure()
plt.plot(months,dataset['Max'], 'ro'), plt.plot(days, yearly_temps(days, *res_max), 'r-')
plt.plot(months,dataset['Min'], 'bo'), plt.plot(days, yearly_temps(days, *res_min), 'b-')
plt.xlabel('Month'), plt.ylabel('Temperature ($^\circ$C)')
plt.plot(months,dataset['Min'],'bo')
plt.show()
