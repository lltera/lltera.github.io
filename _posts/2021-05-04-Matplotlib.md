---
layout: splash
title:  "Numpy operation"
subtitle: "Numpy operation"
categories:
    - data analysis
tags:
    - data analysis
author_profile: true
---
# Matplotlib
## 1. start matplotlib
-  A comprehensive library for creating static, animated, and interactive visualizations in Python.
-  Active by `%matplotlib inline`


```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

%matplotlib inline
```

## 2.  Case Study with Arguments


```python
plt.plot([1,2,3,4,5]) # plotting / y = x +1
plt.show() # displays plt
```


![png](./image/2021-05-04-Matplotlib/output_3_0.png)


### Figsize : Adjusting the size of the frame


```python
plt.figure(figsize=(6,6)) # Declare Frame of plotting
plt.plot([1,2,3,4,5])
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_5_0.png)



```python
plt.figure(figsize=(3,3)) # size 3, 3
plt.plot([1,2,3,4,5])
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_6_0.png)


### Graphing Quadratic Equations with plot()


```python
# y = x
plt.plot([0,1,2,3,4])
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_8_0.png)



```python
# graphing with numpy.array
# y = x^2
x = np.array([1,2,3,4,5])# domain
y = np.array([1,4,9,16,25])# f(x)

plt.plot(x,y)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_9_0.png)



```python
# np.arange(a,b,c)
x = np.arange(-10,10,0.01)
plt.plot(x,x**2)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_10_0.png)



```python
# labeling on x and y axis
x = np.arange(-10,10,0.01)

plt.xlabel("x value")
plt.ylabel("f(x) value")

plt.plot(x,x**2)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_11_0.png)



```python
# limit range of x and y axis
x = np.arange(-10,10,0.01)
plt.xlabel("x value")
plt.ylabel("f(x) value")

plt.axis([-5,5,0,25]) # [x_min,x_max,y_min,y_max]

plt.plot(x,x**2)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_12_0.png)



```python
# set x and y axis interval
x = np.arange(-10,10,0.01)
plt.xlabel("x value")
plt.ylabel("f(x) value")
plt.axis([-5,5,0,25])

plt.xticks([i for i in range(-5,6,1)]) # set x axis interval, -5, -4, .... , 4, 5
plt.yticks([i for i in range(0,27,3)]) # set y axis interval

plt.plot(x,x**2)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_13_0.png)



```python
# put Title !
x = np.arange(-10,10,0.01)
plt.xlabel("x value")
plt.ylabel("f(x) value")
plt.axis([-5,5,0,25])
plt.xticks([i for i in range(-5,6,1)])
plt.yticks([i for i in range(0,27,3)])

plt.title("y = x^2 graph") # title
plt.plot(x,x**2, label = "trend") # legend of this plot
plt.legend() # plot legend on graph

plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_14_0.png)


## 3.  Matplotlib Case Study

### line graph ( Plot )


```python
x = np.arange(20) # 0 ~ 19
y = np.random.randint(0, 10, 20) # Generate random numbers between 1 and 9, 20 times.

plt.plot(x,y)

plt.axis([0,20,0,10])
plt.yticks([i for i in range(11)])

plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_16_0.png)


### Scatter Plot


```python
plt.scatter(x,y)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_18_0.png)


### Box Plot
![boxplot](https://aiaspirant.com/wp-content/uploads/2019/07/box-and-whisker-plot.jpg)


```python
plt.boxplot(y)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_20_0.png)


### Bar Plot


```python
plt.bar(x,y)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_22_0.png)



```python
# set xtics again
plt.bar(x,y)
plt.xticks(np.arange(0,20,1))
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_23_0.png)


### Histogram
-  an approximate representation of the distribution of numerical data


```python
plt.hist(y, bins = np.arange(0,10,2))
plt.xticks(np.arange(0,10,2))
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_25_0.png)


### Pie Chart
-  useful to see the ratio


```python
z = [100, 300, 200, 400]
plt.pie(z, labels = ['one','two','three','four'])
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_27_0.png)


## 4.  Seaborn
###  Python data visualization library based on matplotlib
-  Kernel Density Plot
-  Count Plot
-  Cat Plot
-  Strip Plot
-  Hitmap Plot


```python
import seaborn as sns
```

### Kernel Density Plot
-  Graphs Continuous Distributions like histogram but in curved line
-  `sns.kdeplot()`


```python
# in HIstogram
x = np.arange(0,22,2)
y = np.random.randint(0,20,20)
plt.hist(y, bins= x)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_31_0.png)



```python
# Kernel Density Plot ( kdeplot )
sns.kdeplot(y)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_32_0.png)



```python
sns.kdeplot(y,shade = True) # Fill graph
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_33_0.png)


### Count Plot
-  Visualize frequency in column
-  `sns.countplot()`


```python
vote_df = pd.DataFrame({"name":['Andy','Bob','Cat'],"vote":[True,True,False]})
vote_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>vote</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Andy</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bob</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cat</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>




```python
# in matplotlib barplot
# figure out the number of False and True
vote_count = vote_df.groupby('vote').count()
vote_count
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
    </tr>
    <tr>
      <th>vote</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>False</th>
      <td>1</td>
    </tr>
    <tr>
      <th>True</th>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.bar(x=[False,True],height=vote_count['name'])
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_37_0.png)



```python
# usage sns.countplot

sns.countplot(x = vote_df['vote'])
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_38_0.png)


### Cat Plot
-  useful to indicate the relationship between categorical and numerical data
-  `sns.catplot()`


```python
covid = pd.read_csv("./country_wise_latest.csv")
covid.head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country/Region</th>
      <th>Confirmed</th>
      <th>Deaths</th>
      <th>Recovered</th>
      <th>Active</th>
      <th>New cases</th>
      <th>New deaths</th>
      <th>New recovered</th>
      <th>Deaths / 100 Cases</th>
      <th>Recovered / 100 Cases</th>
      <th>Deaths / 100 Recovered</th>
      <th>Confirmed last week</th>
      <th>1 week change</th>
      <th>1 week % increase</th>
      <th>WHO Region</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>36263</td>
      <td>1269</td>
      <td>25198</td>
      <td>9796</td>
      <td>106</td>
      <td>10</td>
      <td>18</td>
      <td>3.50</td>
      <td>69.49</td>
      <td>5.04</td>
      <td>35526</td>
      <td>737</td>
      <td>2.07</td>
      <td>Eastern Mediterranean</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>4880</td>
      <td>144</td>
      <td>2745</td>
      <td>1991</td>
      <td>117</td>
      <td>6</td>
      <td>63</td>
      <td>2.95</td>
      <td>56.25</td>
      <td>5.25</td>
      <td>4171</td>
      <td>709</td>
      <td>17.00</td>
      <td>Europe</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>27973</td>
      <td>1163</td>
      <td>18837</td>
      <td>7973</td>
      <td>616</td>
      <td>8</td>
      <td>749</td>
      <td>4.16</td>
      <td>67.34</td>
      <td>6.17</td>
      <td>23691</td>
      <td>4282</td>
      <td>18.07</td>
      <td>Africa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>907</td>
      <td>52</td>
      <td>803</td>
      <td>52</td>
      <td>10</td>
      <td>0</td>
      <td>0</td>
      <td>5.73</td>
      <td>88.53</td>
      <td>6.48</td>
      <td>884</td>
      <td>23</td>
      <td>2.60</td>
      <td>Europe</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>950</td>
      <td>41</td>
      <td>242</td>
      <td>667</td>
      <td>18</td>
      <td>1</td>
      <td>0</td>
      <td>4.32</td>
      <td>25.47</td>
      <td>16.94</td>
      <td>749</td>
      <td>201</td>
      <td>26.84</td>
      <td>Africa</td>
    </tr>
  </tbody>
</table>
</div>




```python
s = sns.catplot(x='WHO Region',y='Confirmed',data=covid)
s.fig.set_size_inches(10,6)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_41_0.png)


### Strip Plot
-  similar to Scatter plot
-  `sns.stripplot()`


```python
sns.stripplot(x='WHO Region',y='Recovered',data=covid)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_43_0.png)



```python
# cf) swarmplot
sns.swarmplot(x='WHO Region',y='Recovered',data=covid)
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_44_0.png)


### Heatmap
-  Plot a matrix of data in color( useful to show correlations )
- `sns.heatmap()`


```python
covid.corr()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Confirmed</th>
      <th>Deaths</th>
      <th>Recovered</th>
      <th>Active</th>
      <th>New cases</th>
      <th>New deaths</th>
      <th>New recovered</th>
      <th>Deaths / 100 Cases</th>
      <th>Recovered / 100 Cases</th>
      <th>Deaths / 100 Recovered</th>
      <th>Confirmed last week</th>
      <th>1 week change</th>
      <th>1 week % increase</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Confirmed</th>
      <td>1.000000</td>
      <td>0.934698</td>
      <td>0.906377</td>
      <td>0.927018</td>
      <td>0.909720</td>
      <td>0.871683</td>
      <td>0.859252</td>
      <td>0.063550</td>
      <td>-0.064815</td>
      <td>0.025175</td>
      <td>0.999127</td>
      <td>0.954710</td>
      <td>-0.010161</td>
    </tr>
    <tr>
      <th>Deaths</th>
      <td>0.934698</td>
      <td>1.000000</td>
      <td>0.832098</td>
      <td>0.871586</td>
      <td>0.806975</td>
      <td>0.814161</td>
      <td>0.765114</td>
      <td>0.251565</td>
      <td>-0.114529</td>
      <td>0.169006</td>
      <td>0.939082</td>
      <td>0.855330</td>
      <td>-0.034708</td>
    </tr>
    <tr>
      <th>Recovered</th>
      <td>0.906377</td>
      <td>0.832098</td>
      <td>1.000000</td>
      <td>0.682103</td>
      <td>0.818942</td>
      <td>0.820338</td>
      <td>0.919203</td>
      <td>0.048438</td>
      <td>0.026610</td>
      <td>-0.027277</td>
      <td>0.899312</td>
      <td>0.910013</td>
      <td>-0.013697</td>
    </tr>
    <tr>
      <th>Active</th>
      <td>0.927018</td>
      <td>0.871586</td>
      <td>0.682103</td>
      <td>1.000000</td>
      <td>0.851190</td>
      <td>0.781123</td>
      <td>0.673887</td>
      <td>0.054380</td>
      <td>-0.132618</td>
      <td>0.058386</td>
      <td>0.931459</td>
      <td>0.847642</td>
      <td>-0.003752</td>
    </tr>
    <tr>
      <th>New cases</th>
      <td>0.909720</td>
      <td>0.806975</td>
      <td>0.818942</td>
      <td>0.851190</td>
      <td>1.000000</td>
      <td>0.935947</td>
      <td>0.914765</td>
      <td>0.020104</td>
      <td>-0.078666</td>
      <td>-0.011637</td>
      <td>0.896084</td>
      <td>0.959993</td>
      <td>0.030791</td>
    </tr>
    <tr>
      <th>New deaths</th>
      <td>0.871683</td>
      <td>0.814161</td>
      <td>0.820338</td>
      <td>0.781123</td>
      <td>0.935947</td>
      <td>1.000000</td>
      <td>0.889234</td>
      <td>0.060399</td>
      <td>-0.062792</td>
      <td>-0.020750</td>
      <td>0.862118</td>
      <td>0.894915</td>
      <td>0.025293</td>
    </tr>
    <tr>
      <th>New recovered</th>
      <td>0.859252</td>
      <td>0.765114</td>
      <td>0.919203</td>
      <td>0.673887</td>
      <td>0.914765</td>
      <td>0.889234</td>
      <td>1.000000</td>
      <td>0.017090</td>
      <td>-0.024293</td>
      <td>-0.023340</td>
      <td>0.839692</td>
      <td>0.954321</td>
      <td>0.032662</td>
    </tr>
    <tr>
      <th>Deaths / 100 Cases</th>
      <td>0.063550</td>
      <td>0.251565</td>
      <td>0.048438</td>
      <td>0.054380</td>
      <td>0.020104</td>
      <td>0.060399</td>
      <td>0.017090</td>
      <td>1.000000</td>
      <td>-0.168920</td>
      <td>0.334594</td>
      <td>0.069894</td>
      <td>0.015095</td>
      <td>-0.134534</td>
    </tr>
    <tr>
      <th>Recovered / 100 Cases</th>
      <td>-0.064815</td>
      <td>-0.114529</td>
      <td>0.026610</td>
      <td>-0.132618</td>
      <td>-0.078666</td>
      <td>-0.062792</td>
      <td>-0.024293</td>
      <td>-0.168920</td>
      <td>1.000000</td>
      <td>-0.295381</td>
      <td>-0.064600</td>
      <td>-0.063013</td>
      <td>-0.394254</td>
    </tr>
    <tr>
      <th>Deaths / 100 Recovered</th>
      <td>0.025175</td>
      <td>0.169006</td>
      <td>-0.027277</td>
      <td>0.058386</td>
      <td>-0.011637</td>
      <td>-0.020750</td>
      <td>-0.023340</td>
      <td>0.334594</td>
      <td>-0.295381</td>
      <td>1.000000</td>
      <td>0.030460</td>
      <td>-0.013763</td>
      <td>-0.049083</td>
    </tr>
    <tr>
      <th>Confirmed last week</th>
      <td>0.999127</td>
      <td>0.939082</td>
      <td>0.899312</td>
      <td>0.931459</td>
      <td>0.896084</td>
      <td>0.862118</td>
      <td>0.839692</td>
      <td>0.069894</td>
      <td>-0.064600</td>
      <td>0.030460</td>
      <td>1.000000</td>
      <td>0.941448</td>
      <td>-0.015247</td>
    </tr>
    <tr>
      <th>1 week change</th>
      <td>0.954710</td>
      <td>0.855330</td>
      <td>0.910013</td>
      <td>0.847642</td>
      <td>0.959993</td>
      <td>0.894915</td>
      <td>0.954321</td>
      <td>0.015095</td>
      <td>-0.063013</td>
      <td>-0.013763</td>
      <td>0.941448</td>
      <td>1.000000</td>
      <td>0.026594</td>
    </tr>
    <tr>
      <th>1 week % increase</th>
      <td>-0.010161</td>
      <td>-0.034708</td>
      <td>-0.013697</td>
      <td>-0.003752</td>
      <td>0.030791</td>
      <td>0.025293</td>
      <td>0.032662</td>
      <td>-0.134534</td>
      <td>-0.394254</td>
      <td>-0.049083</td>
      <td>-0.015247</td>
      <td>0.026594</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
sns.heatmap(covid.corr())
plt.show()
```


![png](./image/2021-05-04-Matplotlib/output_47_0.png)
