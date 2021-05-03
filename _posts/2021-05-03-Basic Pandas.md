# Pandas

## 1. How to start Pandas
### prerequisite : Table
-  Data structures(container) that store and manage data using rows and columns
-  Normaly rows represent objects and columns represent properties

[covid dataset](https://www.kaggle.com/imdevskp/corona-virus-report)

### start Pandas
`import pandas`


```python
import pandas as pd
```

## 2. 1-D Data handling Using Pandas - Series
### Series?

-  1-D labeled **array**
-  possible to indicate index


```python
s = pd.Series([1,4,9,16,25])
s
```




    0     1
    1     4
    2     9
    3    16
    4    25
    dtype: int64




```python
t = pd.Series({'one':1,'two':2,'three':3,'four':4,'five':5})
t
```




    one      1
    two      2
    three    3
    four     4
    five     5
    dtype: int64



### Series + Numpy
-  Series is similar to ndarray


```python
s[1]
```




    4




```python
t[1]
```




    2




```python
t[1:3]
```




    two      2
    three    3
    dtype: int64




```python
s[ s > s.median()] # Extract only values bigger than own median values
```




    3    16
    4    25
    dtype: int64




```python
s[[3,1,4]]
```




    3    16
    1     4
    4    25
    dtype: int64




```python
import numpy as np
np.exp(s)
```




    0    2.718282e+00
    1    5.459815e+01
    2    8.103084e+03
    3    8.886111e+06
    4    7.200490e+10
    dtype: float64




```python
s.dtype
```




    dtype('int64')



### Series + dict
-  Series is similar to **dict**


```python
t
```




    one      1
    two      2
    three    3
    four     4
    five     5
    dtype: int64




```python
t['one']
```




    1




```python
# add key and value in Series
t['six'] = 6
t
```




    one      1
    two      2
    three    3
    four     4
    five     5
    six      6
    dtype: int64




```python
'six' in t # check 'six' is in t or not
```




    True




```python
'seven' in t
```




    False




```python
t.get('seven') # if 'seven' is not in t return None
```


```python
t.get('seven',0) # if 'seven' is not in t return None
```




    0



### Naming in Series




```python
s = pd.Series(np.random.randn(5), name="random_nums")
s
```




    0    0.474883
    1   -0.758169
    2    1.912442
    3   -0.197958
    4    0.898772
    Name: random_nums, dtype: float64




```python
s.name = "random value"
s
```




    0    0.474883
    1   -0.758169
    2    1.912442
    3   -0.197958
    4    0.898772
    Name: random value, dtype: float64



## 2. 2-D Data handling Using Pandas - Dataframe
### dataframe?
-  2-D labeled **table**
-  able to indicate index


```python
d = {"height":[1,2,3,4], "weight":[30,40,50,60]}
df = pd.DataFrame(d)
df
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
      <th>height</th>
      <th>weight</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>30</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>40</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>50</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>60</td>
    </tr>
  </tbody>
</table>
</div>




```python
## data type
df.dtypes
```




    height    int64
    weight    int64
    dtype: object



## From CSV to dataframe
-  Data frames can be configured via Comma Separated Value(csv)
-  `.read_csv()`


```python
# csv file need to be located in same directory

covid = pd.read_csv("./country_wise_latest.csv")
covid
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
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>182</th>
      <td>West Bank and Gaza</td>
      <td>10621</td>
      <td>78</td>
      <td>3752</td>
      <td>6791</td>
      <td>152</td>
      <td>2</td>
      <td>0</td>
      <td>0.73</td>
      <td>35.33</td>
      <td>2.08</td>
      <td>8916</td>
      <td>1705</td>
      <td>19.12</td>
      <td>Eastern Mediterranean</td>
    </tr>
    <tr>
      <th>183</th>
      <td>Western Sahara</td>
      <td>10</td>
      <td>1</td>
      <td>8</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>10.00</td>
      <td>80.00</td>
      <td>12.50</td>
      <td>10</td>
      <td>0</td>
      <td>0.00</td>
      <td>Africa</td>
    </tr>
    <tr>
      <th>184</th>
      <td>Yemen</td>
      <td>1691</td>
      <td>483</td>
      <td>833</td>
      <td>375</td>
      <td>10</td>
      <td>4</td>
      <td>36</td>
      <td>28.56</td>
      <td>49.26</td>
      <td>57.98</td>
      <td>1619</td>
      <td>72</td>
      <td>4.45</td>
      <td>Eastern Mediterranean</td>
    </tr>
    <tr>
      <th>185</th>
      <td>Zambia</td>
      <td>4552</td>
      <td>140</td>
      <td>2815</td>
      <td>1597</td>
      <td>71</td>
      <td>1</td>
      <td>465</td>
      <td>3.08</td>
      <td>61.84</td>
      <td>4.97</td>
      <td>3326</td>
      <td>1226</td>
      <td>36.86</td>
      <td>Africa</td>
    </tr>
    <tr>
      <th>186</th>
      <td>Zimbabwe</td>
      <td>2704</td>
      <td>36</td>
      <td>542</td>
      <td>2126</td>
      <td>192</td>
      <td>2</td>
      <td>24</td>
      <td>1.33</td>
      <td>20.04</td>
      <td>6.64</td>
      <td>1713</td>
      <td>991</td>
      <td>57.85</td>
      <td>Africa</td>
    </tr>
  </tbody>
</table>
<p>187 rows × 15 columns</p>
</div>



### Applications of Pandas 
#### 1.Observing a fraction of the data


```python
covid.head(5) # to observe 5 from the top
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
covid.tail(5) # to observe 5 from the bottom
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
      <th>182</th>
      <td>West Bank and Gaza</td>
      <td>10621</td>
      <td>78</td>
      <td>3752</td>
      <td>6791</td>
      <td>152</td>
      <td>2</td>
      <td>0</td>
      <td>0.73</td>
      <td>35.33</td>
      <td>2.08</td>
      <td>8916</td>
      <td>1705</td>
      <td>19.12</td>
      <td>Eastern Mediterranean</td>
    </tr>
    <tr>
      <th>183</th>
      <td>Western Sahara</td>
      <td>10</td>
      <td>1</td>
      <td>8</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>10.00</td>
      <td>80.00</td>
      <td>12.50</td>
      <td>10</td>
      <td>0</td>
      <td>0.00</td>
      <td>Africa</td>
    </tr>
    <tr>
      <th>184</th>
      <td>Yemen</td>
      <td>1691</td>
      <td>483</td>
      <td>833</td>
      <td>375</td>
      <td>10</td>
      <td>4</td>
      <td>36</td>
      <td>28.56</td>
      <td>49.26</td>
      <td>57.98</td>
      <td>1619</td>
      <td>72</td>
      <td>4.45</td>
      <td>Eastern Mediterranean</td>
    </tr>
    <tr>
      <th>185</th>
      <td>Zambia</td>
      <td>4552</td>
      <td>140</td>
      <td>2815</td>
      <td>1597</td>
      <td>71</td>
      <td>1</td>
      <td>465</td>
      <td>3.08</td>
      <td>61.84</td>
      <td>4.97</td>
      <td>3326</td>
      <td>1226</td>
      <td>36.86</td>
      <td>Africa</td>
    </tr>
    <tr>
      <th>186</th>
      <td>Zimbabwe</td>
      <td>2704</td>
      <td>36</td>
      <td>542</td>
      <td>2126</td>
      <td>192</td>
      <td>2</td>
      <td>24</td>
      <td>1.33</td>
      <td>20.04</td>
      <td>6.64</td>
      <td>1713</td>
      <td>991</td>
      <td>57.85</td>
      <td>Africa</td>
    </tr>
  </tbody>
</table>
</div>



#### 2. Access to the data

-  `df['column_name']` or `df.column_name`


```python
covid['Active']
```




    0      9796
    1      1991
    2      7973
    3        52
    4       667
           ... 
    182    6791
    183       1
    184     375
    185    1597
    186    2126
    Name: Active, Length: 187, dtype: int64




```python
covid.Active
```




    0      9796
    1      1991
    2      7973
    3        52
    4       667
           ... 
    182    6791
    183       1
    184     375
    185    1597
    186    2126
    Name: Active, Length: 187, dtype: int64




```python
covid.WHO Region # when blank is in key
```


      File "<ipython-input-35-1174247fd45e>", line 1
        covid.WHO Region
                  ^
    SyntaxError: invalid syntax
    



```python
covid['WHO Region']
```




    0      Eastern Mediterranean
    1                     Europe
    2                     Africa
    3                     Europe
    4                     Africa
                   ...          
    182    Eastern Mediterranean
    183                   Africa
    184    Eastern Mediterranean
    185                   Africa
    186                   Africa
    Name: WHO Region, Length: 187, dtype: object



#### Tips!  Each column in Dataframe is "Series"


```python
type(covid['Confirmed']) #
```




    pandas.core.series.Series




```python
covid['Confirmed'][0]
```




    36263




```python
covid['Confirmed'][1:5]
```




    1     4880
    2    27973
    3      907
    4      950
    Name: Confirmed, dtype: int64



#### 3. Acess to the data with "Conditions"


```python
# if i want to know some countries that over 100 new confirmed cases
covid['New cases'] > 100
```




    0       True
    1       True
    2       True
    3      False
    4      False
           ...  
    182     True
    183    False
    184    False
    185    False
    186     True
    Name: New cases, Length: 187, dtype: bool




```python
covid[covid['New cases'] > 100]
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
      <th>6</th>
      <td>Argentina</td>
      <td>167416</td>
      <td>3059</td>
      <td>72575</td>
      <td>91782</td>
      <td>4890</td>
      <td>120</td>
      <td>2057</td>
      <td>1.83</td>
      <td>43.35</td>
      <td>4.21</td>
      <td>130774</td>
      <td>36642</td>
      <td>28.02</td>
      <td>Americas</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Australia</td>
      <td>15303</td>
      <td>167</td>
      <td>9311</td>
      <td>5825</td>
      <td>368</td>
      <td>6</td>
      <td>137</td>
      <td>1.09</td>
      <td>60.84</td>
      <td>1.79</td>
      <td>12428</td>
      <td>2875</td>
      <td>23.13</td>
      <td>Western Pacific</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>177</th>
      <td>United Kingdom</td>
      <td>301708</td>
      <td>45844</td>
      <td>1437</td>
      <td>254427</td>
      <td>688</td>
      <td>7</td>
      <td>3</td>
      <td>15.19</td>
      <td>0.48</td>
      <td>3190.26</td>
      <td>296944</td>
      <td>4764</td>
      <td>1.60</td>
      <td>Europe</td>
    </tr>
    <tr>
      <th>179</th>
      <td>Uzbekistan</td>
      <td>21209</td>
      <td>121</td>
      <td>11674</td>
      <td>9414</td>
      <td>678</td>
      <td>5</td>
      <td>569</td>
      <td>0.57</td>
      <td>55.04</td>
      <td>1.04</td>
      <td>17149</td>
      <td>4060</td>
      <td>23.67</td>
      <td>Europe</td>
    </tr>
    <tr>
      <th>180</th>
      <td>Venezuela</td>
      <td>15988</td>
      <td>146</td>
      <td>9959</td>
      <td>5883</td>
      <td>525</td>
      <td>4</td>
      <td>213</td>
      <td>0.91</td>
      <td>62.29</td>
      <td>1.47</td>
      <td>12334</td>
      <td>3654</td>
      <td>29.63</td>
      <td>Americas</td>
    </tr>
    <tr>
      <th>182</th>
      <td>West Bank and Gaza</td>
      <td>10621</td>
      <td>78</td>
      <td>3752</td>
      <td>6791</td>
      <td>152</td>
      <td>2</td>
      <td>0</td>
      <td>0.73</td>
      <td>35.33</td>
      <td>2.08</td>
      <td>8916</td>
      <td>1705</td>
      <td>19.12</td>
      <td>Eastern Mediterranean</td>
    </tr>
    <tr>
      <th>186</th>
      <td>Zimbabwe</td>
      <td>2704</td>
      <td>36</td>
      <td>542</td>
      <td>2126</td>
      <td>192</td>
      <td>2</td>
      <td>24</td>
      <td>1.33</td>
      <td>20.04</td>
      <td>6.64</td>
      <td>1713</td>
      <td>991</td>
      <td>57.85</td>
      <td>Africa</td>
    </tr>
  </tbody>
</table>
<p>82 rows × 15 columns</p>
</div>




```python
# to Find countries where WHO region is South-East Asia
# first Find Categories in 'WHO region' column
covid['WHO Region'].unique()
```




    array(['Eastern Mediterranean', 'Europe', 'Africa', 'Americas',
           'Western Pacific', 'South-East Asia'], dtype=object)




```python
covid['WHO Region'] == 'South-East Asia'
```




    0      False
    1      False
    2      False
    3      False
    4      False
           ...  
    182    False
    183    False
    184    False
    185    False
    186    False
    Name: WHO Region, Length: 187, dtype: bool




```python
covid[covid['WHO Region'] == 'South-East Asia']
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
      <th>13</th>
      <td>Bangladesh</td>
      <td>226225</td>
      <td>2965</td>
      <td>125683</td>
      <td>97577</td>
      <td>2772</td>
      <td>37</td>
      <td>1801</td>
      <td>1.31</td>
      <td>55.56</td>
      <td>2.36</td>
      <td>207453</td>
      <td>18772</td>
      <td>9.05</td>
      <td>South-East Asia</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Bhutan</td>
      <td>99</td>
      <td>0</td>
      <td>86</td>
      <td>13</td>
      <td>4</td>
      <td>0</td>
      <td>1</td>
      <td>0.00</td>
      <td>86.87</td>
      <td>0.00</td>
      <td>90</td>
      <td>9</td>
      <td>10.00</td>
      <td>South-East Asia</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Burma</td>
      <td>350</td>
      <td>6</td>
      <td>292</td>
      <td>52</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>1.71</td>
      <td>83.43</td>
      <td>2.05</td>
      <td>341</td>
      <td>9</td>
      <td>2.64</td>
      <td>South-East Asia</td>
    </tr>
    <tr>
      <th>79</th>
      <td>India</td>
      <td>1480073</td>
      <td>33408</td>
      <td>951166</td>
      <td>495499</td>
      <td>44457</td>
      <td>637</td>
      <td>33598</td>
      <td>2.26</td>
      <td>64.26</td>
      <td>3.51</td>
      <td>1155338</td>
      <td>324735</td>
      <td>28.11</td>
      <td>South-East Asia</td>
    </tr>
    <tr>
      <th>80</th>
      <td>Indonesia</td>
      <td>100303</td>
      <td>4838</td>
      <td>58173</td>
      <td>37292</td>
      <td>1525</td>
      <td>57</td>
      <td>1518</td>
      <td>4.82</td>
      <td>58.00</td>
      <td>8.32</td>
      <td>88214</td>
      <td>12089</td>
      <td>13.70</td>
      <td>South-East Asia</td>
    </tr>
    <tr>
      <th>106</th>
      <td>Maldives</td>
      <td>3369</td>
      <td>15</td>
      <td>2547</td>
      <td>807</td>
      <td>67</td>
      <td>0</td>
      <td>19</td>
      <td>0.45</td>
      <td>75.60</td>
      <td>0.59</td>
      <td>2999</td>
      <td>370</td>
      <td>12.34</td>
      <td>South-East Asia</td>
    </tr>
    <tr>
      <th>119</th>
      <td>Nepal</td>
      <td>18752</td>
      <td>48</td>
      <td>13754</td>
      <td>4950</td>
      <td>139</td>
      <td>3</td>
      <td>626</td>
      <td>0.26</td>
      <td>73.35</td>
      <td>0.35</td>
      <td>17844</td>
      <td>908</td>
      <td>5.09</td>
      <td>South-East Asia</td>
    </tr>
    <tr>
      <th>158</th>
      <td>Sri Lanka</td>
      <td>2805</td>
      <td>11</td>
      <td>2121</td>
      <td>673</td>
      <td>23</td>
      <td>0</td>
      <td>15</td>
      <td>0.39</td>
      <td>75.61</td>
      <td>0.52</td>
      <td>2730</td>
      <td>75</td>
      <td>2.75</td>
      <td>South-East Asia</td>
    </tr>
    <tr>
      <th>167</th>
      <td>Thailand</td>
      <td>3297</td>
      <td>58</td>
      <td>3111</td>
      <td>128</td>
      <td>6</td>
      <td>0</td>
      <td>2</td>
      <td>1.76</td>
      <td>94.36</td>
      <td>1.86</td>
      <td>3250</td>
      <td>47</td>
      <td>1.45</td>
      <td>South-East Asia</td>
    </tr>
    <tr>
      <th>168</th>
      <td>Timor-Leste</td>
      <td>24</td>
      <td>0</td>
      <td>0</td>
      <td>24</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>24</td>
      <td>0</td>
      <td>0.00</td>
      <td>South-East Asia</td>
    </tr>
  </tbody>
</table>
</div>



#### 4. Accessing data based on rows


```python
# ex - books imformation
books_dict = {"Available":[True,True,False], "Location":[102,215,323], "Genre":["Programming","Physics","Mathematics"]}
books_df = pd.DataFrame(books_dict, index = ['What is the Bug?','DokiDoki Physics','Derivative Slayer'])
books_df
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
      <th>Available</th>
      <th>Location</th>
      <th>Genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>What is the Bug?</th>
      <td>True</td>
      <td>102</td>
      <td>Programming</td>
    </tr>
    <tr>
      <th>DokiDoki Physics</th>
      <td>True</td>
      <td>215</td>
      <td>Physics</td>
    </tr>
    <tr>
      <th>Derivative Slayer</th>
      <td>False</td>
      <td>323</td>
      <td>Mathematics</td>
    </tr>
  </tbody>
</table>
</div>



derive from using indexes : `.loc[row,col]`


```python
books_df.loc["What is the Bug?"]
```




    Available           True
    Location             102
    Genre        Programming
    Name: What is the Bug?, dtype: object




```python
# If i want to know that 'Derivative Slayer' is available.

books_df.loc["Derivative Slayer",'Available']
```




    False



derive from using number indexes : `.iloc[row_idx,col_idx]`


```python
books_df.iloc[0,1]
```




    102




```python
#[1, 0~1]
books_df.iloc[1,0:2]
```




    Available    True
    Location      215
    Name: DokiDoki Physics, dtype: object



#### 5. groupby
-  Split : Splits data based on specific standard
-  Apply : Apply a statistical function to compress each data - sum(), mean(), median()
-  Combine : Combine a new Series based on applied results(group_key:applied_value)  

`.groupby()`


```python
# Number of confirmed cases by WHO region
# 1. extract confirmed cases coulmn only from dataframe covid
# 2. The extracted column groupby by WHO region.
covid_by_region = covid['Confirmed'].groupby(by = covid["WHO Region"])
covid_by_region
```




    <pandas.core.groupby.generic.SeriesGroupBy object at 0x000001EFE7B62FA0>




```python
covid_by_region.sum()
```




    WHO Region
    Africa                    723207
    Americas                 8839286
    Eastern Mediterranean    1490744
    Europe                   3299523
    South-East Asia          1835297
    Western Pacific           292428
    Name: Confirmed, dtype: int64




```python
# Average number of confirmed cases by WHO region
covid_by_region.mean() # sum() /  number of countries in each regions
```




    WHO Region
    Africa                    15066.812500
    Americas                 252551.028571
    Eastern Mediterranean     67761.090909
    Europe                    58920.053571
    South-East Asia          183529.700000
    Western Pacific           18276.750000
    Name: Confirmed, dtype: float64




```python

```
