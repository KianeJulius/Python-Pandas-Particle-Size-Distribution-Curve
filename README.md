# Python-Pandas-Particle-Size-Distribution-Curve

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

Load the data


```python
df = pd.read_excel("D:/ACADEMICS/1. FOURTH YEAR, SECOND SEM/Construction Materials and Testing/particle size distribution.xlsx")
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
      <th>Unnamed: 0</th>
      <th>Unnamed: 1</th>
      <th>Unnamed: 2</th>
      <th>Unnamed: 3</th>
      <th>Unnamed: 4</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
      <th>Unnamed: 7</th>
      <th>Unnamed: 8</th>
      <th>Unnamed: 9</th>
      <th>Unnamed: 10</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>a</td>
      <td>the percent finer than each sieve and plot</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>grain size distribution curve (from the forms ...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>b</td>
      <td>D10, D30, D60 from the distribution curve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>NaN</td>
      <td>c</td>
      <td>the uniformity coefficient</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>NaN</td>
      <td>d</td>
      <td>coefficient of gradation</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>NaN</td>
      <td>Sieve No.</td>
      <td>Sieve Size</td>
      <td>Mass of Soil Retained</td>
      <td>Percent Retained on Each Sieve</td>
      <td>Cumulative % retained on each sieve</td>
      <td>Percent finer</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
      <td>NaN</td>
      <td>D10</td>
      <td>1.437631</td>
      <td>mm</td>
    </tr>
    <tr>
      <th>10</th>
      <td>NaN</td>
      <td>10</td>
      <td>2</td>
      <td>30</td>
      <td>4.398827</td>
      <td>4.398827</td>
      <td>95.601173</td>
      <td>NaN</td>
      <td>D30</td>
      <td>0.170468</td>
      <td>mm</td>
    </tr>
    <tr>
      <th>11</th>
      <td>NaN</td>
      <td>20</td>
      <td>0.85</td>
      <td>55</td>
      <td>8.064516</td>
      <td>12.463343</td>
      <td>87.536657</td>
      <td>NaN</td>
      <td>D60</td>
      <td>0.259229</td>
      <td>mm</td>
    </tr>
    <tr>
      <th>12</th>
      <td>NaN</td>
      <td>40</td>
      <td>0.425</td>
      <td>76</td>
      <td>11.143695</td>
      <td>23.607038</td>
      <td>76.392962</td>
      <td>NaN</td>
      <td>Cc</td>
      <td>0.077975</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13</th>
      <td>NaN</td>
      <td>60</td>
      <td>0.25</td>
      <td>120</td>
      <td>17.595308</td>
      <td>41.202346</td>
      <td>58.797654</td>
      <td>NaN</td>
      <td>Cu</td>
      <td>0.180317</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14</th>
      <td>NaN</td>
      <td>80</td>
      <td>0.18</td>
      <td>140</td>
      <td>20.527859</td>
      <td>61.730205</td>
      <td>38.269795</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>NaN</td>
      <td>100</td>
      <td>0.15</td>
      <td>189</td>
      <td>27.71261</td>
      <td>89.442815</td>
      <td>10.557185</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>NaN</td>
      <td>200</td>
      <td>0.075</td>
      <td>62</td>
      <td>9.090909</td>
      <td>98.533724</td>
      <td>1.466276</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>17</th>
      <td>NaN</td>
      <td>Pan</td>
      <td>NaN</td>
      <td>10</td>
      <td>1.466276</td>
      <td>100</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>NaN</td>
      <td>Total</td>
      <td>NaN</td>
      <td>682</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>20</th>
      <td>NaN</td>
      <td>Sieve No.</td>
      <td>Sieve Size</td>
      <td>Mass of Soil Retained</td>
      <td>Percent Retained on Each Sieve</td>
      <td>Cumulative % retained on each sieve</td>
      <td>Percent finer</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>21</th>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
      <td>NaN</td>
      <td>D10</td>
      <td>0.152765</td>
      <td>mm</td>
    </tr>
    <tr>
      <th>22</th>
      <td>NaN</td>
      <td>10</td>
      <td>2</td>
      <td>25</td>
      <td>3.481894</td>
      <td>3.481894</td>
      <td>96.518106</td>
      <td>NaN</td>
      <td>D30</td>
      <td>0.170613</td>
      <td>mm</td>
    </tr>
    <tr>
      <th>23</th>
      <td>NaN</td>
      <td>20</td>
      <td>0.85</td>
      <td>48</td>
      <td>6.685237</td>
      <td>10.167131</td>
      <td>89.832869</td>
      <td>NaN</td>
      <td>D60</td>
      <td>0.269171</td>
      <td>mm</td>
    </tr>
    <tr>
      <th>24</th>
      <td>NaN</td>
      <td>40</td>
      <td>0.425</td>
      <td>98</td>
      <td>13.649025</td>
      <td>23.816156</td>
      <td>76.183844</td>
      <td>NaN</td>
      <td>Cc</td>
      <td>0.707902</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25</th>
      <td>NaN</td>
      <td>60</td>
      <td>0.25</td>
      <td>135</td>
      <td>18.802228</td>
      <td>42.618384</td>
      <td>57.381616</td>
      <td>NaN</td>
      <td>Cu</td>
      <td>1.761992</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>26</th>
      <td>NaN</td>
      <td>80</td>
      <td>0.18</td>
      <td>127</td>
      <td>17.688022</td>
      <td>60.306407</td>
      <td>39.693593</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>27</th>
      <td>NaN</td>
      <td>100</td>
      <td>0.15</td>
      <td>235</td>
      <td>32.729805</td>
      <td>93.036212</td>
      <td>6.963788</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>28</th>
      <td>NaN</td>
      <td>200</td>
      <td>0.075</td>
      <td>42</td>
      <td>5.849582</td>
      <td>98.885794</td>
      <td>1.114206</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>29</th>
      <td>NaN</td>
      <td>Pan</td>
      <td>NaN</td>
      <td>8</td>
      <td>1.114206</td>
      <td>100.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>30</th>
      <td>NaN</td>
      <td>Total</td>
      <td>NaN</td>
      <td>718</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>31</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>32</th>
      <td>NaN</td>
      <td>Sieve No.</td>
      <td>Sieve Size</td>
      <td>Mass of Soil Retained</td>
      <td>Percent Retained on Each Sieve</td>
      <td>Cumulative % retained on each sieve</td>
      <td>Percent finer</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>33</th>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
      <td>NaN</td>
      <td>D10</td>
      <td>0.148362</td>
      <td>mm</td>
    </tr>
    <tr>
      <th>34</th>
      <td>NaN</td>
      <td>10</td>
      <td>2</td>
      <td>32</td>
      <td>4.500703</td>
      <td>4.500703</td>
      <td>95.499297</td>
      <td>NaN</td>
      <td>D30</td>
      <td>0.169094</td>
      <td>mm</td>
    </tr>
    <tr>
      <th>35</th>
      <td>NaN</td>
      <td>20</td>
      <td>0.85</td>
      <td>54</td>
      <td>7.594937</td>
      <td>12.09564</td>
      <td>87.90436</td>
      <td>NaN</td>
      <td>D60</td>
      <td>0.246426</td>
      <td>mm</td>
    </tr>
    <tr>
      <th>36</th>
      <td>NaN</td>
      <td>40</td>
      <td>0.425</td>
      <td>87</td>
      <td>12.236287</td>
      <td>24.331927</td>
      <td>75.668073</td>
      <td>NaN</td>
      <td>Cc</td>
      <td>0.782075</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>37</th>
      <td>NaN</td>
      <td>60</td>
      <td>0.25</td>
      <td>105</td>
      <td>14.767932</td>
      <td>39.099859</td>
      <td>60.900141</td>
      <td>NaN</td>
      <td>Cu</td>
      <td>1.660980</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>38</th>
      <td>NaN</td>
      <td>80</td>
      <td>0.18</td>
      <td>146</td>
      <td>20.534459</td>
      <td>59.634318</td>
      <td>40.365682</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>39</th>
      <td>NaN</td>
      <td>100</td>
      <td>0.15</td>
      <td>215</td>
      <td>30.2391</td>
      <td>89.873418</td>
      <td>10.126582</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>40</th>
      <td>NaN</td>
      <td>200</td>
      <td>0.075</td>
      <td>57</td>
      <td>8.016878</td>
      <td>97.890295</td>
      <td>2.109705</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>41</th>
      <td>NaN</td>
      <td>Pan</td>
      <td>NaN</td>
      <td>15</td>
      <td>2.109705</td>
      <td>100</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>42</th>
      <td>NaN</td>
      <td>Total</td>
      <td>NaN</td>
      <td>711</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Cut the columns


```python
dfmain = df[['Unnamed: 1','Unnamed: 2','Unnamed: 3','Unnamed: 4','Unnamed: 5','Unnamed: 6']]
dfmain
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
      <th>Unnamed: 1</th>
      <th>Unnamed: 2</th>
      <th>Unnamed: 3</th>
      <th>Unnamed: 4</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>a</td>
      <td>the percent finer than each sieve and plot</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>grain size distribution curve (from the forms ...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>b</td>
      <td>D10, D30, D60 from the distribution curve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>c</td>
      <td>the uniformity coefficient</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>d</td>
      <td>coefficient of gradation</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Sieve No.</td>
      <td>Sieve Size</td>
      <td>Mass of Soil Retained</td>
      <td>Percent Retained on Each Sieve</td>
      <td>Cumulative % retained on each sieve</td>
      <td>Percent finer</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>2</td>
      <td>30</td>
      <td>4.398827</td>
      <td>4.398827</td>
      <td>95.601173</td>
    </tr>
    <tr>
      <th>11</th>
      <td>20</td>
      <td>0.85</td>
      <td>55</td>
      <td>8.064516</td>
      <td>12.463343</td>
      <td>87.536657</td>
    </tr>
    <tr>
      <th>12</th>
      <td>40</td>
      <td>0.425</td>
      <td>76</td>
      <td>11.143695</td>
      <td>23.607038</td>
      <td>76.392962</td>
    </tr>
    <tr>
      <th>13</th>
      <td>60</td>
      <td>0.25</td>
      <td>120</td>
      <td>17.595308</td>
      <td>41.202346</td>
      <td>58.797654</td>
    </tr>
    <tr>
      <th>14</th>
      <td>80</td>
      <td>0.18</td>
      <td>140</td>
      <td>20.527859</td>
      <td>61.730205</td>
      <td>38.269795</td>
    </tr>
    <tr>
      <th>15</th>
      <td>100</td>
      <td>0.15</td>
      <td>189</td>
      <td>27.71261</td>
      <td>89.442815</td>
      <td>10.557185</td>
    </tr>
    <tr>
      <th>16</th>
      <td>200</td>
      <td>0.075</td>
      <td>62</td>
      <td>9.090909</td>
      <td>98.533724</td>
      <td>1.466276</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Pan</td>
      <td>NaN</td>
      <td>10</td>
      <td>1.466276</td>
      <td>100</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Total</td>
      <td>NaN</td>
      <td>682</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Sieve No.</td>
      <td>Sieve Size</td>
      <td>Mass of Soil Retained</td>
      <td>Percent Retained on Each Sieve</td>
      <td>Cumulative % retained on each sieve</td>
      <td>Percent finer</td>
    </tr>
    <tr>
      <th>21</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
    </tr>
    <tr>
      <th>22</th>
      <td>10</td>
      <td>2</td>
      <td>25</td>
      <td>3.481894</td>
      <td>3.481894</td>
      <td>96.518106</td>
    </tr>
    <tr>
      <th>23</th>
      <td>20</td>
      <td>0.85</td>
      <td>48</td>
      <td>6.685237</td>
      <td>10.167131</td>
      <td>89.832869</td>
    </tr>
    <tr>
      <th>24</th>
      <td>40</td>
      <td>0.425</td>
      <td>98</td>
      <td>13.649025</td>
      <td>23.816156</td>
      <td>76.183844</td>
    </tr>
    <tr>
      <th>25</th>
      <td>60</td>
      <td>0.25</td>
      <td>135</td>
      <td>18.802228</td>
      <td>42.618384</td>
      <td>57.381616</td>
    </tr>
    <tr>
      <th>26</th>
      <td>80</td>
      <td>0.18</td>
      <td>127</td>
      <td>17.688022</td>
      <td>60.306407</td>
      <td>39.693593</td>
    </tr>
    <tr>
      <th>27</th>
      <td>100</td>
      <td>0.15</td>
      <td>235</td>
      <td>32.729805</td>
      <td>93.036212</td>
      <td>6.963788</td>
    </tr>
    <tr>
      <th>28</th>
      <td>200</td>
      <td>0.075</td>
      <td>42</td>
      <td>5.849582</td>
      <td>98.885794</td>
      <td>1.114206</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Pan</td>
      <td>NaN</td>
      <td>8</td>
      <td>1.114206</td>
      <td>100.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Total</td>
      <td>NaN</td>
      <td>718</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>31</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Sieve No.</td>
      <td>Sieve Size</td>
      <td>Mass of Soil Retained</td>
      <td>Percent Retained on Each Sieve</td>
      <td>Cumulative % retained on each sieve</td>
      <td>Percent finer</td>
    </tr>
    <tr>
      <th>33</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
    </tr>
    <tr>
      <th>34</th>
      <td>10</td>
      <td>2</td>
      <td>32</td>
      <td>4.500703</td>
      <td>4.500703</td>
      <td>95.499297</td>
    </tr>
    <tr>
      <th>35</th>
      <td>20</td>
      <td>0.85</td>
      <td>54</td>
      <td>7.594937</td>
      <td>12.09564</td>
      <td>87.90436</td>
    </tr>
    <tr>
      <th>36</th>
      <td>40</td>
      <td>0.425</td>
      <td>87</td>
      <td>12.236287</td>
      <td>24.331927</td>
      <td>75.668073</td>
    </tr>
    <tr>
      <th>37</th>
      <td>60</td>
      <td>0.25</td>
      <td>105</td>
      <td>14.767932</td>
      <td>39.099859</td>
      <td>60.900141</td>
    </tr>
    <tr>
      <th>38</th>
      <td>80</td>
      <td>0.18</td>
      <td>146</td>
      <td>20.534459</td>
      <td>59.634318</td>
      <td>40.365682</td>
    </tr>
    <tr>
      <th>39</th>
      <td>100</td>
      <td>0.15</td>
      <td>215</td>
      <td>30.2391</td>
      <td>89.873418</td>
      <td>10.126582</td>
    </tr>
    <tr>
      <th>40</th>
      <td>200</td>
      <td>0.075</td>
      <td>57</td>
      <td>8.016878</td>
      <td>97.890295</td>
      <td>2.109705</td>
    </tr>
    <tr>
      <th>41</th>
      <td>Pan</td>
      <td>NaN</td>
      <td>15</td>
      <td>2.109705</td>
      <td>100</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>42</th>
      <td>Total</td>
      <td>NaN</td>
      <td>711</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Rename the columns


```python
dfmain= dfmain.rename(columns={'Unnamed: 1':'Sieve No','Unnamed: 2':'Sieve Size,mm',
                          'Unnamed: 3':'Mass Retained', 'Unnamed: 4':'Percent Retained',
                          'Unnamed: 5':'Cumm.Percent','Unnamed: 6':'Percent Finer'})
dfmain
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
      <th>Sieve No</th>
      <th>Sieve Size,mm</th>
      <th>Mass Retained</th>
      <th>Percent Retained</th>
      <th>Cumm.Percent</th>
      <th>Percent Finer</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>a</td>
      <td>the percent finer than each sieve and plot</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>grain size distribution curve (from the forms ...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>b</td>
      <td>D10, D30, D60 from the distribution curve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>c</td>
      <td>the uniformity coefficient</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>d</td>
      <td>coefficient of gradation</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Sieve No.</td>
      <td>Sieve Size</td>
      <td>Mass of Soil Retained</td>
      <td>Percent Retained on Each Sieve</td>
      <td>Cumulative % retained on each sieve</td>
      <td>Percent finer</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>2</td>
      <td>30</td>
      <td>4.398827</td>
      <td>4.398827</td>
      <td>95.601173</td>
    </tr>
    <tr>
      <th>11</th>
      <td>20</td>
      <td>0.85</td>
      <td>55</td>
      <td>8.064516</td>
      <td>12.463343</td>
      <td>87.536657</td>
    </tr>
    <tr>
      <th>12</th>
      <td>40</td>
      <td>0.425</td>
      <td>76</td>
      <td>11.143695</td>
      <td>23.607038</td>
      <td>76.392962</td>
    </tr>
    <tr>
      <th>13</th>
      <td>60</td>
      <td>0.25</td>
      <td>120</td>
      <td>17.595308</td>
      <td>41.202346</td>
      <td>58.797654</td>
    </tr>
    <tr>
      <th>14</th>
      <td>80</td>
      <td>0.18</td>
      <td>140</td>
      <td>20.527859</td>
      <td>61.730205</td>
      <td>38.269795</td>
    </tr>
    <tr>
      <th>15</th>
      <td>100</td>
      <td>0.15</td>
      <td>189</td>
      <td>27.71261</td>
      <td>89.442815</td>
      <td>10.557185</td>
    </tr>
    <tr>
      <th>16</th>
      <td>200</td>
      <td>0.075</td>
      <td>62</td>
      <td>9.090909</td>
      <td>98.533724</td>
      <td>1.466276</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Pan</td>
      <td>NaN</td>
      <td>10</td>
      <td>1.466276</td>
      <td>100</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Total</td>
      <td>NaN</td>
      <td>682</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Sieve No.</td>
      <td>Sieve Size</td>
      <td>Mass of Soil Retained</td>
      <td>Percent Retained on Each Sieve</td>
      <td>Cumulative % retained on each sieve</td>
      <td>Percent finer</td>
    </tr>
    <tr>
      <th>21</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
    </tr>
    <tr>
      <th>22</th>
      <td>10</td>
      <td>2</td>
      <td>25</td>
      <td>3.481894</td>
      <td>3.481894</td>
      <td>96.518106</td>
    </tr>
    <tr>
      <th>23</th>
      <td>20</td>
      <td>0.85</td>
      <td>48</td>
      <td>6.685237</td>
      <td>10.167131</td>
      <td>89.832869</td>
    </tr>
    <tr>
      <th>24</th>
      <td>40</td>
      <td>0.425</td>
      <td>98</td>
      <td>13.649025</td>
      <td>23.816156</td>
      <td>76.183844</td>
    </tr>
    <tr>
      <th>25</th>
      <td>60</td>
      <td>0.25</td>
      <td>135</td>
      <td>18.802228</td>
      <td>42.618384</td>
      <td>57.381616</td>
    </tr>
    <tr>
      <th>26</th>
      <td>80</td>
      <td>0.18</td>
      <td>127</td>
      <td>17.688022</td>
      <td>60.306407</td>
      <td>39.693593</td>
    </tr>
    <tr>
      <th>27</th>
      <td>100</td>
      <td>0.15</td>
      <td>235</td>
      <td>32.729805</td>
      <td>93.036212</td>
      <td>6.963788</td>
    </tr>
    <tr>
      <th>28</th>
      <td>200</td>
      <td>0.075</td>
      <td>42</td>
      <td>5.849582</td>
      <td>98.885794</td>
      <td>1.114206</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Pan</td>
      <td>NaN</td>
      <td>8</td>
      <td>1.114206</td>
      <td>100.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Total</td>
      <td>NaN</td>
      <td>718</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>31</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Sieve No.</td>
      <td>Sieve Size</td>
      <td>Mass of Soil Retained</td>
      <td>Percent Retained on Each Sieve</td>
      <td>Cumulative % retained on each sieve</td>
      <td>Percent finer</td>
    </tr>
    <tr>
      <th>33</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
    </tr>
    <tr>
      <th>34</th>
      <td>10</td>
      <td>2</td>
      <td>32</td>
      <td>4.500703</td>
      <td>4.500703</td>
      <td>95.499297</td>
    </tr>
    <tr>
      <th>35</th>
      <td>20</td>
      <td>0.85</td>
      <td>54</td>
      <td>7.594937</td>
      <td>12.09564</td>
      <td>87.90436</td>
    </tr>
    <tr>
      <th>36</th>
      <td>40</td>
      <td>0.425</td>
      <td>87</td>
      <td>12.236287</td>
      <td>24.331927</td>
      <td>75.668073</td>
    </tr>
    <tr>
      <th>37</th>
      <td>60</td>
      <td>0.25</td>
      <td>105</td>
      <td>14.767932</td>
      <td>39.099859</td>
      <td>60.900141</td>
    </tr>
    <tr>
      <th>38</th>
      <td>80</td>
      <td>0.18</td>
      <td>146</td>
      <td>20.534459</td>
      <td>59.634318</td>
      <td>40.365682</td>
    </tr>
    <tr>
      <th>39</th>
      <td>100</td>
      <td>0.15</td>
      <td>215</td>
      <td>30.2391</td>
      <td>89.873418</td>
      <td>10.126582</td>
    </tr>
    <tr>
      <th>40</th>
      <td>200</td>
      <td>0.075</td>
      <td>57</td>
      <td>8.016878</td>
      <td>97.890295</td>
      <td>2.109705</td>
    </tr>
    <tr>
      <th>41</th>
      <td>Pan</td>
      <td>NaN</td>
      <td>15</td>
      <td>2.109705</td>
      <td>100</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>42</th>
      <td>Total</td>
      <td>NaN</td>
      <td>711</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Separate the dataset into three DataFrames


```python
df1 = dfmain.iloc[9:17,0:10]
df1.reset_index(inplace=True,drop=True)
df1
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
      <th>Sieve No</th>
      <th>Sieve Size,mm</th>
      <th>Mass Retained</th>
      <th>Percent Retained</th>
      <th>Cumm.Percent</th>
      <th>Percent Finer</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10</td>
      <td>2</td>
      <td>30</td>
      <td>4.398827</td>
      <td>4.398827</td>
      <td>95.601173</td>
    </tr>
    <tr>
      <th>2</th>
      <td>20</td>
      <td>0.85</td>
      <td>55</td>
      <td>8.064516</td>
      <td>12.463343</td>
      <td>87.536657</td>
    </tr>
    <tr>
      <th>3</th>
      <td>40</td>
      <td>0.425</td>
      <td>76</td>
      <td>11.143695</td>
      <td>23.607038</td>
      <td>76.392962</td>
    </tr>
    <tr>
      <th>4</th>
      <td>60</td>
      <td>0.25</td>
      <td>120</td>
      <td>17.595308</td>
      <td>41.202346</td>
      <td>58.797654</td>
    </tr>
    <tr>
      <th>5</th>
      <td>80</td>
      <td>0.18</td>
      <td>140</td>
      <td>20.527859</td>
      <td>61.730205</td>
      <td>38.269795</td>
    </tr>
    <tr>
      <th>6</th>
      <td>100</td>
      <td>0.15</td>
      <td>189</td>
      <td>27.71261</td>
      <td>89.442815</td>
      <td>10.557185</td>
    </tr>
    <tr>
      <th>7</th>
      <td>200</td>
      <td>0.075</td>
      <td>62</td>
      <td>9.090909</td>
      <td>98.533724</td>
      <td>1.466276</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = dfmain.iloc[21:29,0:10]
df2.reset_index(inplace=True,drop=True)
df2
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
      <th>Sieve No</th>
      <th>Sieve Size,mm</th>
      <th>Mass Retained</th>
      <th>Percent Retained</th>
      <th>Cumm.Percent</th>
      <th>Percent Finer</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10</td>
      <td>2</td>
      <td>25</td>
      <td>3.481894</td>
      <td>3.481894</td>
      <td>96.518106</td>
    </tr>
    <tr>
      <th>2</th>
      <td>20</td>
      <td>0.85</td>
      <td>48</td>
      <td>6.685237</td>
      <td>10.167131</td>
      <td>89.832869</td>
    </tr>
    <tr>
      <th>3</th>
      <td>40</td>
      <td>0.425</td>
      <td>98</td>
      <td>13.649025</td>
      <td>23.816156</td>
      <td>76.183844</td>
    </tr>
    <tr>
      <th>4</th>
      <td>60</td>
      <td>0.25</td>
      <td>135</td>
      <td>18.802228</td>
      <td>42.618384</td>
      <td>57.381616</td>
    </tr>
    <tr>
      <th>5</th>
      <td>80</td>
      <td>0.18</td>
      <td>127</td>
      <td>17.688022</td>
      <td>60.306407</td>
      <td>39.693593</td>
    </tr>
    <tr>
      <th>6</th>
      <td>100</td>
      <td>0.15</td>
      <td>235</td>
      <td>32.729805</td>
      <td>93.036212</td>
      <td>6.963788</td>
    </tr>
    <tr>
      <th>7</th>
      <td>200</td>
      <td>0.075</td>
      <td>42</td>
      <td>5.849582</td>
      <td>98.885794</td>
      <td>1.114206</td>
    </tr>
  </tbody>
</table>
</div>




```python
df3 = dfmain.iloc[33:41,0:10]
df3.reset_index(inplace=True,drop=True)
df3
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
      <th>Sieve No</th>
      <th>Sieve Size,mm</th>
      <th>Mass Retained</th>
      <th>Percent Retained</th>
      <th>Cumm.Percent</th>
      <th>Percent Finer</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>100</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10</td>
      <td>2</td>
      <td>32</td>
      <td>4.500703</td>
      <td>4.500703</td>
      <td>95.499297</td>
    </tr>
    <tr>
      <th>2</th>
      <td>20</td>
      <td>0.85</td>
      <td>54</td>
      <td>7.594937</td>
      <td>12.09564</td>
      <td>87.90436</td>
    </tr>
    <tr>
      <th>3</th>
      <td>40</td>
      <td>0.425</td>
      <td>87</td>
      <td>12.236287</td>
      <td>24.331927</td>
      <td>75.668073</td>
    </tr>
    <tr>
      <th>4</th>
      <td>60</td>
      <td>0.25</td>
      <td>105</td>
      <td>14.767932</td>
      <td>39.099859</td>
      <td>60.900141</td>
    </tr>
    <tr>
      <th>5</th>
      <td>80</td>
      <td>0.18</td>
      <td>146</td>
      <td>20.534459</td>
      <td>59.634318</td>
      <td>40.365682</td>
    </tr>
    <tr>
      <th>6</th>
      <td>100</td>
      <td>0.15</td>
      <td>215</td>
      <td>30.2391</td>
      <td>89.873418</td>
      <td>10.126582</td>
    </tr>
    <tr>
      <th>7</th>
      <td>200</td>
      <td>0.075</td>
      <td>57</td>
      <td>8.016878</td>
      <td>97.890295</td>
      <td>2.109705</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.rcParams['figure.figsize'] = [10,5]
```


```python
df1['Sieve Size,mm']
```




    0        0
    1        2
    2     0.85
    3    0.425
    4     0.25
    5     0.18
    6     0.15
    7    0.075
    Name: Sieve Size,mm, dtype: object




```python
from scipy.interpolate import make_interp_spline
```


```python
x = df1['Sieve Size,mm']
y = df1['Percent Finer']

plt.semilogx(x,y)
plt.semilogx(x,y,'o')

xcoords = df1['Sieve Size,mm']
for xc in xcoords:
    plt.axvline(x=xc, c='black')

plt.ylim(0,100)
plt.xlim(0,50)
plt.xlabel("Sieve Size (mm)")
plt.ylabel("Percent Passing")
plt.title("Particle Size Distribution Curve")

plt.show()
```

    C:\Users\kiane\AppData\Local\Temp\ipykernel_21472\3149034666.py:12: UserWarning: Attempted to set non-positive left xlim on a log-scaled axis.
    Invalid limit will be ignored.
      plt.xlim(0,50)
    


    
![png](https://user-images.githubusercontent.com/124150494/224320000-9a549d95-27dd-4079-8590-a79ac8cb5a63.png)
    



```python
x = df2['Sieve Size,mm']
y = df2['Percent Finer']

plt.semilogx(x,y)
plt.semilogx(x,y,'o')

xcoords = df2['Sieve Size,mm']
for xc in xcoords:
    plt.axvline(x=xc, c='black')

plt.ylim(0,100)
plt.xlim(0,50)
plt.xlabel("Sieve Size (mm)")
plt.ylabel("Percent Passing")
plt.title("Particle Size Distribution Curve")

plt.show()
```

    C:\Users\kiane\AppData\Local\Temp\ipykernel_21472\2418293726.py:12: UserWarning: Attempted to set non-positive left xlim on a log-scaled axis.
    Invalid limit will be ignored.
      plt.xlim(0,50)
    


    
![png](https://user-images.githubusercontent.com/124150494/224319955-5c9691ec-1fb9-4c4e-aaa6-b4c37a0891d9.png)
    



```python
x = df3['Sieve Size,mm']
y = df3['Percent Finer']

plt.semilogx(x,y)
plt.semilogx(x,y,'o')

xcoords = df3['Sieve Size,mm']
for xc in xcoords:
    plt.axvline(x=xc, c='black')

plt.ylim(0,100)
plt.xlim(0,50)
plt.xlabel("Sieve Size (mm)")
plt.ylabel("Percent Passing")
plt.title("Particle Size Distribution Curve")

plt.show()
```

    C:\Users\kiane\AppData\Local\Temp\ipykernel_21472\2098524903.py:12: UserWarning: Attempted to set non-positive left xlim on a log-scaled axis.
    Invalid limit will be ignored.
      plt.xlim(0,50)
    


    
![png](https://user-images.githubusercontent.com/124150494/224320022-b19a65da-2a0c-46b2-830b-81d423465944.png)
    

