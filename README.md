# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
            



```python
import pandas as pd
df = pd.read_csv("SAMPLEIDS.csv")
df

```





<div id="df-a5756c21-35ea-4998-8c39-bc6408edcae4" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>1</td>
<td>1220121</td>
<td>ARUN</td>
<td>2000-02-10</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>82.0</td>
<td>81.0</td>
<td>90.0</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
</tr>
<tr>
<th>1</th>
<td>2</td>
<td>1220122</td>
<td>BABU</td>
<td>1999-01-25</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>56.0</td>
<td>61.0</td>
<td>80.0</td>
<td>56.0</td>
<td>253.0</td>
<td>84.333333</td>
</tr>
<tr>
<th>2</th>
<td>3</td>
<td>1220123</td>
<td>CHARAN</td>
<td>2000.09.21</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>NaN</td>
<td>59.0</td>
<td>60.0</td>
<td>70.0</td>
<td>NaN</td>
<td>0.000000</td>
</tr>
<tr>
<th>3</th>
<td>4</td>
<td>1220124</td>
<td>DEVA</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>74.0</td>
<td>79.0</td>
<td>80.0</td>
<td>74.0</td>
<td>307.0</td>
<td>102.333333</td>
</tr>
<tr>
<th>4</th>
<td>5</td>
<td>1220125</td>
<td>ESTER</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>92.0</td>
<td>95.0</td>
<td>96.0</td>
<td>92.0</td>
<td>375.0</td>
<td>125.000000</td>
</tr>
<tr>
<th>5</th>
<td>6</td>
<td>1220126</td>
<td>FARHANA</td>
<td>1999-03-05</td>
<td>FEMALE</td>
<td>THANDALAM</td>
<td>91.0</td>
<td>88.0</td>
<td>90.0</td>
<td>91.0</td>
<td>360.0</td>
<td>120.000000</td>
</tr>
<tr>
<th>6</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>1220128</td>
<td>HEMA</td>
<td>1999-01-25</td>
<td>FEMALE</td>
<td>POONAMALEE</td>
<td>95.0</td>
<td>96.0</td>
<td>90.0</td>
<td>95.0</td>
<td>376.0</td>
<td>125.333333</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>1220129</td>
<td>INDRA</td>
<td>2000.09.21</td>
<td>FEMALE</td>
<td>KANCHIPURAM</td>
<td>64.0</td>
<td>NaN</td>
<td>NaN</td>
<td>64.0</td>
<td>NaN</td>
<td>0.000000</td>
</tr>
<tr>
<th>10</th>
<td>10</td>
<td>1220130</td>
<td>JAHITH</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>34.0</td>
<td>45.0</td>
<td>50.0</td>
<td>34.0</td>
<td>163.0</td>
<td>54.333333</td>
</tr>
<tr>
<th>11</th>
<td>11</td>
<td>1220131</td>
<td>KANI</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>96.0</td>
<td>95.0</td>
<td>96.0</td>
<td>96.0</td>
<td>383.0</td>
<td>127.666667</td>
</tr>
<tr>
<th>12</th>
<td>12</td>
<td>1220132</td>
<td>LATHESSH</td>
<td>1999-03-05</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>NaN</td>
<td>68.0</td>
<td>70.0</td>
<td>70.0</td>
<td>208.0</td>
<td>69.333333</td>
</tr>
<tr>
<th>13</th>
<td>13</td>
<td>1220133</td>
<td>MANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>71.0</td>
<td>76.0</td>
<td>NaN</td>
<td>71.0</td>
<td>NaN</td>
<td>0.000000</td>
</tr>
<tr>
<th>14</th>
<td>14</td>
<td>1220134</td>
<td>NANI</td>
<td>20001109</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>79.0</td>
<td>77.0</td>
<td>80.0</td>
<td>79.0</td>
<td>315.0</td>
<td>105.000000</td>
</tr>
<tr>
<th>15</th>
<td>15</td>
<td>1220135</td>
<td>NaN</td>
<td>19990125</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>0.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>16</th>
<td>16</td>
<td>1220136</td>
<td>PRATHAP</td>
<td>20000921</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>86.0</td>
<td>84.0</td>
<td>90.0</td>
<td>86.0</td>
<td>346.0</td>
<td>115.333333</td>
</tr>
<tr>
<th>17</th>
<td>17</td>
<td>1220137</td>
<td>RAGHU</td>
<td>20001109</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>67.0</td>
<td>64.0</td>
<td>70.0</td>
<td>NaN</td>
<td>201.0</td>
<td>67.000000</td>
</tr>
<tr>
<th>18</th>
<td>18</td>
<td>1220138</td>
<td>RATHI</td>
<td>20001121</td>
<td>FEMALE</td>
<td>KANCHIPURAM</td>
<td>81.0</td>
<td>86.0</td>
<td>90.0</td>
<td>81.0</td>
<td>338.0</td>
<td>112.666667</td>
</tr>
<tr>
<th>19</th>
<td>19</td>
<td>1220139</td>
<td>SARVESH</td>
<td>19990305</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>84.0</td>
<td>87.0</td>
<td>NaN</td>
<td>84.0</td>
<td>NaN</td>
<td>0.000000</td>
</tr>
<tr>
<th>20</th>
<td>20</td>
<td>1220140</td>
<td>SANTHOSH</td>
<td>20001002</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>76.0</td>
<td>69.0</td>
<td>80.0</td>
<td>76.0</td>
<td>301.0</td>
<td>100.333333</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-a5756c21-35ea-4998-8c39-bc6408edcae4')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


<div id="id_7f3fa723-3e90-4aa5-a735-1b356130ecf8">
```




(21, 12)




```python


```


```python
df.head(2)
```





<div id="df-c53f211d-e27e-4f6a-b493-263494a98bf8" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>1</td>
<td>1220121</td>
<td>ARUN</td>
<td>2000-02-10</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>82.0</td>
<td>81.0</td>
<td>90.0</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
</tr>
<tr>
<th>1</th>
<td>2</td>
<td>1220122</td>
<td>BABU</td>
<td>1999-01-25</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>56.0</td>
<td>61.0</td>
<td>80.0</td>
<td>56.0</td>
<td>253.0</td>
<td>84.333333</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-c53f211d-e27e-4f6a-b493-263494a98bf8')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.tail(2)
```





<div id="df-c45e402e-080d-43fa-b2a8-a092b6051d72" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>19</th>
<td>19</td>
<td>1220139</td>
<td>SARVESH</td>
<td>19990305</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>84.0</td>
<td>87.0</td>
<td>NaN</td>
<td>84.0</td>
<td>NaN</td>
<td>0.000000</td>
</tr>
<tr>
<th>20</th>
<td>20</td>
<td>1220140</td>
<td>SANTHOSH</td>
<td>20001002</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>76.0</td>
<td>69.0</td>
<td>80.0</td>
<td>76.0</td>
<td>301.0</td>
<td>100.333333</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-c45e402e-080d-43fa-b2a8-a092b6051d72')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.describe()
```





<div id="df-61b1a28f-1dba-494a-a6fe-8839a00de3d5" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>count</th>
<td>21.000000</td>
<td>2.100000e+01</td>
<td>18.000000</td>
<td>19.000000</td>
<td>17.000000</td>
<td>18.000000</td>
<td>16.000000</td>
<td>20.000000</td>
</tr>
<tr>
<th>mean</th>
<td>10.333333</td>
<td>1.220130e+06</td>
<td>73.666667</td>
<td>74.315789</td>
<td>79.529412</td>
<td>73.166667</td>
<td>272.750000</td>
<td>72.733333</td>
</tr>
<tr>
<th>std</th>
<td>5.816643</td>
<td>5.816643e+00</td>
<td>17.580069</td>
<td>15.836149</td>
<td>13.010177</td>
<td>17.426315</td>
<td>102.048681</td>
<td>48.017127</td>
</tr>
<tr>
<th>min</th>
<td>1.000000</td>
<td>1.220121e+06</td>
<td>34.000000</td>
<td>45.000000</td>
<td>50.000000</td>
<td>34.000000</td>
<td>0.000000</td>
<td>0.000000</td>
</tr>
<tr>
<th>25%</th>
<td>6.000000</td>
<td>1.220126e+06</td>
<td>64.750000</td>
<td>62.500000</td>
<td>70.000000</td>
<td>65.500000</td>
<td>216.250000</td>
<td>40.750000</td>
</tr>
<tr>
<th>50%</th>
<td>10.000000</td>
<td>1.220130e+06</td>
<td>77.500000</td>
<td>77.000000</td>
<td>80.000000</td>
<td>75.000000</td>
<td>304.000000</td>
<td>78.666667</td>
</tr>
<tr>
<th>75%</th>
<td>15.000000</td>
<td>1.220135e+06</td>
<td>85.500000</td>
<td>86.500000</td>
<td>90.000000</td>
<td>85.500000</td>
<td>349.500000</td>
<td>113.333333</td>
</tr>
<tr>
<th>max</th>
<td>20.000000</td>
<td>1.220140e+06</td>
<td>96.000000</td>
<td>96.000000</td>
<td>96.000000</td>
<td>96.000000</td>
<td>383.000000</td>
<td>127.666667</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-61b1a28f-1dba-494a-a6fe-8839a00de3d5')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.info()

```

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 21 entries, 0 to 20
Data columns (total 12 columns):
#   Column   Non-Null Count  Dtype  
---  ------   --------------  -----  
0   SNO      21 non-null     int64  
1   REGNO    21 non-null     int64  
2   NAME     20 non-null     object 
3   DOB      21 non-null     object 
4   GENDER   20 non-null     object 
5   ADDRESS  20 non-null     object 
6   M1       18 non-null     float64
7   M2       19 non-null     float64
8   M3       17 non-null     float64
9   M4       18 non-null     float64
10  TOTAL    16 non-null     float64
11  AVG      20 non-null     float64
dtypes: float64(6), int64(2), object(4)
memory usage: 2.1+ KB



```python
df.isnull()
```





<div id="df-7b482fce-bdd7-480f-ba88-30c3d95c342b" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>1</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>2</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>True</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>True</td>
<td>False</td>
</tr>
<tr>
<th>3</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>4</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>5</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>6</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>7</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>8</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>9</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>True</td>
<td>True</td>
<td>False</td>
<td>True</td>
<td>False</td>
</tr>
<tr>
<th>10</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>11</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>12</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>True</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>13</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>True</td>
<td>False</td>
<td>True</td>
<td>False</td>
</tr>
<tr>
<th>14</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>15</th>
<td>False</td>
<td>False</td>
<td>True</td>
<td>False</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>16</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>17</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>True</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>18</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>19</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>True</td>
<td>False</td>
<td>True</td>
<td>False</td>
</tr>
<tr>
<th>20</th>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-7b482fce-bdd7-480f-ba88-30c3d95c342b')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.notnull()
```





<div id="df-f896b969-aefc-4d32-8100-58f6808f9d06" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>False</td>
<td>False</td>
<td>False</td>
</tr>
<tr>
<th>1</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>2</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>False</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>False</td>
<td>True</td>
</tr>
<tr>
<th>3</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>4</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>5</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>6</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>7</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>8</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>9</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>False</td>
<td>False</td>
<td>True</td>
<td>False</td>
<td>True</td>
</tr>
<tr>
<th>10</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>11</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>12</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>False</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>13</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>False</td>
<td>True</td>
<td>False</td>
<td>True</td>
</tr>
<tr>
<th>14</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>15</th>
<td>True</td>
<td>True</td>
<td>False</td>
<td>True</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>False</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>16</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>17</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>False</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>18</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
<tr>
<th>19</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>False</td>
<td>True</td>
<td>False</td>
<td>True</td>
</tr>
<tr>
<th>20</th>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
<td>True</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-f896b969-aefc-4d32-8100-58f6808f9d06')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.dropna(axis=0) #remove the specif row
```





<div id="df-8282f2ca-8f24-419d-b19c-91290dd5a51f" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>1</th>
<td>2</td>
<td>1220122</td>
<td>BABU</td>
<td>1999-01-25</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>56.0</td>
<td>61.0</td>
<td>80.0</td>
<td>56.0</td>
<td>253.0</td>
<td>84.333333</td>
</tr>
<tr>
<th>3</th>
<td>4</td>
<td>1220124</td>
<td>DEVA</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>74.0</td>
<td>79.0</td>
<td>80.0</td>
<td>74.0</td>
<td>307.0</td>
<td>102.333333</td>
</tr>
<tr>
<th>4</th>
<td>5</td>
<td>1220125</td>
<td>ESTER</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>92.0</td>
<td>95.0</td>
<td>96.0</td>
<td>92.0</td>
<td>375.0</td>
<td>125.000000</td>
</tr>
<tr>
<th>5</th>
<td>6</td>
<td>1220126</td>
<td>FARHANA</td>
<td>1999-03-05</td>
<td>FEMALE</td>
<td>THANDALAM</td>
<td>91.0</td>
<td>88.0</td>
<td>90.0</td>
<td>91.0</td>
<td>360.0</td>
<td>120.000000</td>
</tr>
<tr>
<th>6</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>1220128</td>
<td>HEMA</td>
<td>1999-01-25</td>
<td>FEMALE</td>
<td>POONAMALEE</td>
<td>95.0</td>
<td>96.0</td>
<td>90.0</td>
<td>95.0</td>
<td>376.0</td>
<td>125.333333</td>
</tr>
<tr>
<th>10</th>
<td>10</td>
<td>1220130</td>
<td>JAHITH</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>34.0</td>
<td>45.0</td>
<td>50.0</td>
<td>34.0</td>
<td>163.0</td>
<td>54.333333</td>
</tr>
<tr>
<th>11</th>
<td>11</td>
<td>1220131</td>
<td>KANI</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>96.0</td>
<td>95.0</td>
<td>96.0</td>
<td>96.0</td>
<td>383.0</td>
<td>127.666667</td>
</tr>
<tr>
<th>14</th>
<td>14</td>
<td>1220134</td>
<td>NANI</td>
<td>20001109</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>79.0</td>
<td>77.0</td>
<td>80.0</td>
<td>79.0</td>
<td>315.0</td>
<td>105.000000</td>
</tr>
<tr>
<th>16</th>
<td>16</td>
<td>1220136</td>
<td>PRATHAP</td>
<td>20000921</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>86.0</td>
<td>84.0</td>
<td>90.0</td>
<td>86.0</td>
<td>346.0</td>
<td>115.333333</td>
</tr>
<tr>
<th>18</th>
<td>18</td>
<td>1220138</td>
<td>RATHI</td>
<td>20001121</td>
<td>FEMALE</td>
<td>KANCHIPURAM</td>
<td>81.0</td>
<td>86.0</td>
<td>90.0</td>
<td>81.0</td>
<td>338.0</td>
<td>112.666667</td>
</tr>
<tr>
<th>20</th>
<td>20</td>
<td>1220140</td>
<td>SANTHOSH</td>
<td>20001002</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>76.0</td>
<td>69.0</td>
<td>80.0</td>
<td>76.0</td>
<td>301.0</td>
<td>100.333333</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-8282f2ca-8f24-419d-b19c-91290dd5a51f')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.dropna(axis=1)  #remove the specif column
```





<div id="df-637c7e39-be73-4b59-953c-249041ad2fb7" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>DOB</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>1</td>
<td>1220121</td>
<td>2000-02-10</td>
</tr>
<tr>
<th>1</th>
<td>2</td>
<td>1220122</td>
<td>1999-01-25</td>
</tr>
<tr>
<th>2</th>
<td>3</td>
<td>1220123</td>
<td>2000.09.21</td>
</tr>
<tr>
<th>3</th>
<td>4</td>
<td>1220124</td>
<td>2000-11-09</td>
</tr>
<tr>
<th>4</th>
<td>5</td>
<td>1220125</td>
<td>2000-11-21</td>
</tr>
<tr>
<th>5</th>
<td>6</td>
<td>1220126</td>
<td>1999-03-05</td>
</tr>
<tr>
<th>6</th>
<td>7</td>
<td>1220127</td>
<td>2000-10-02</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>1220127</td>
<td>2000-10-02</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>1220128</td>
<td>1999-01-25</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>1220129</td>
<td>2000.09.21</td>
</tr>
<tr>
<th>10</th>
<td>10</td>
<td>1220130</td>
<td>2000-11-09</td>
</tr>
<tr>
<th>11</th>
<td>11</td>
<td>1220131</td>
<td>2000-11-21</td>
</tr>
<tr>
<th>12</th>
<td>12</td>
<td>1220132</td>
<td>1999-03-05</td>
</tr>
<tr>
<th>13</th>
<td>13</td>
<td>1220133</td>
<td>2000-10-02</td>
</tr>
<tr>
<th>14</th>
<td>14</td>
<td>1220134</td>
<td>20001109</td>
</tr>
<tr>
<th>15</th>
<td>15</td>
<td>1220135</td>
<td>19990125</td>
</tr>
<tr>
<th>16</th>
<td>16</td>
<td>1220136</td>
<td>20000921</td>
</tr>
<tr>
<th>17</th>
<td>17</td>
<td>1220137</td>
<td>20001109</td>
</tr>
<tr>
<th>18</th>
<td>18</td>
<td>1220138</td>
<td>20001121</td>
</tr>
<tr>
<th>19</th>
<td>19</td>
<td>1220139</td>
<td>19990305</td>
</tr>
<tr>
<th>20</th>
<td>20</td>
<td>1220140</td>
<td>20001002</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-637c7e39-be73-4b59-953c-249041ad2fb7')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
dfs = df[df['ADDRESS']=='THANDALAM']
dfs
```





<div id="df-ec0b4a4b-a1d4-437e-8434-d14b909e4a7a" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>1</td>
<td>1220121</td>
<td>ARUN</td>
<td>2000-02-10</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>82.0</td>
<td>81.0</td>
<td>90.0</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
</tr>
<tr>
<th>2</th>
<td>3</td>
<td>1220123</td>
<td>CHARAN</td>
<td>2000.09.21</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>NaN</td>
<td>59.0</td>
<td>60.0</td>
<td>70.0</td>
<td>NaN</td>
<td>0.000000</td>
</tr>
<tr>
<th>5</th>
<td>6</td>
<td>1220126</td>
<td>FARHANA</td>
<td>1999-03-05</td>
<td>FEMALE</td>
<td>THANDALAM</td>
<td>91.0</td>
<td>88.0</td>
<td>90.0</td>
<td>91.0</td>
<td>360.0</td>
<td>120.000000</td>
</tr>
<tr>
<th>10</th>
<td>10</td>
<td>1220130</td>
<td>JAHITH</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>34.0</td>
<td>45.0</td>
<td>50.0</td>
<td>34.0</td>
<td>163.0</td>
<td>54.333333</td>
</tr>
<tr>
<th>12</th>
<td>12</td>
<td>1220132</td>
<td>LATHESSH</td>
<td>1999-03-05</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>NaN</td>
<td>68.0</td>
<td>70.0</td>
<td>70.0</td>
<td>208.0</td>
<td>69.333333</td>
</tr>
<tr>
<th>19</th>
<td>19</td>
<td>1220139</td>
<td>SARVESH</td>
<td>19990305</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>84.0</td>
<td>87.0</td>
<td>NaN</td>
<td>84.0</td>
<td>NaN</td>
<td>0.000000</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-ec0b4a4b-a1d4-437e-8434-d14b909e4a7a')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


<div id="id_d1127f47-d386-497d-8184-2c89fc3199ed">
4] #extract the specif rows
```





<div id="df-ff78626f-043a-4037-9391-1a74dafe8659" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>sepal_length</th>
<th>sepal_width</th>
<th>petal_length</th>
<th>petal_width</th>
<th>species</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>5.1</td>
<td>3.5</td>
<td>1.4</td>
<td>0.2</td>
<td>setosa</td>
</tr>
<tr>
<th>1</th>
<td>4.9</td>
<td>3.0</td>
<td>1.4</td>
<td>0.2</td>
<td>setosa</td>
</tr>
<tr>
<th>2</th>
<td>4.7</td>
<td>3.2</td>
<td>1.3</td>
<td>0.2</td>
<td>setosa</td>
</tr>
<tr>
<th>3</th>
<td>4.6</td>
<td>3.1</td>
<td>1.5</td>
<td>0.2</td>
<td>setosa</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-ff78626f-043a-4037-9391-1a74dafe8659')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.iloc[0:4,1:4] #df.iloc[row,column]
```





<div id="df-1a055479-6120-423e-b106-a940d888ccbd" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>1220121</td>
<td>ARUN</td>
<td>2000-02-10</td>
</tr>
<tr>
<th>1</th>
<td>1220122</td>
<td>BABU</td>
<td>1999-01-25</td>
</tr>
<tr>
<th>2</th>
<td>1220123</td>
<td>CHARAN</td>
<td>2000.09.21</td>
</tr>
<tr>
<th>3</th>
<td>1220124</td>
<td>DEVA</td>
<td>2000-11-09</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-1a055479-6120-423e-b106-a940d888ccbd')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.iloc[[1,12,35],[2,4]]
```





<div id="df-5d81b0fd-593a-488c-b2fe-04dd95892afc" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>petal_length</th>
<th>species</th>
</tr>
</thead>
<tbody>
<tr>
<th>1</th>
<td>1.4</td>
<td>setosa</td>
</tr>
<tr>
<th>12</th>
<td>1.4</td>
<td>setosa</td>
</tr>
<tr>
<th>35</th>
<td>1.2</td>
<td>setosa</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-5d81b0fd-593a-488c-b2fe-04dd95892afc')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.fillna(0) #it will fill the missing value  ->0
```





<div id="df-cdbb56f9-58d5-44b1-86c3-cd7ce0e919a0" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>1</td>
<td>1220121</td>
<td>ARUN</td>
<td>2000-02-10</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>82.0</td>
<td>81.0</td>
<td>90.0</td>
<td>0.0</td>
<td>0.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>1</th>
<td>2</td>
<td>1220122</td>
<td>BABU</td>
<td>1999-01-25</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>56.0</td>
<td>61.0</td>
<td>80.0</td>
<td>56.0</td>
<td>253.0</td>
<td>84.333333</td>
</tr>
<tr>
<th>2</th>
<td>3</td>
<td>1220123</td>
<td>CHARAN</td>
<td>2000.09.21</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>0.0</td>
<td>59.0</td>
<td>60.0</td>
<td>70.0</td>
<td>0.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>3</th>
<td>4</td>
<td>1220124</td>
<td>DEVA</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>74.0</td>
<td>79.0</td>
<td>80.0</td>
<td>74.0</td>
<td>307.0</td>
<td>102.333333</td>
</tr>
<tr>
<th>4</th>
<td>5</td>
<td>1220125</td>
<td>ESTER</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>92.0</td>
<td>95.0</td>
<td>96.0</td>
<td>92.0</td>
<td>375.0</td>
<td>125.000000</td>
</tr>
<tr>
<th>5</th>
<td>6</td>
<td>1220126</td>
<td>FARHANA</td>
<td>1999-03-05</td>
<td>FEMALE</td>
<td>THANDALAM</td>
<td>91.0</td>
<td>88.0</td>
<td>90.0</td>
<td>91.0</td>
<td>360.0</td>
<td>120.000000</td>
</tr>
<tr>
<th>6</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>1220128</td>
<td>HEMA</td>
<td>1999-01-25</td>
<td>FEMALE</td>
<td>POONAMALEE</td>
<td>95.0</td>
<td>96.0</td>
<td>90.0</td>
<td>95.0</td>
<td>376.0</td>
<td>125.333333</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>1220129</td>
<td>INDRA</td>
<td>2000.09.21</td>
<td>FEMALE</td>
<td>KANCHIPURAM</td>
<td>64.0</td>
<td>0.0</td>
<td>0.0</td>
<td>64.0</td>
<td>0.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>10</th>
<td>10</td>
<td>1220130</td>
<td>JAHITH</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>34.0</td>
<td>45.0</td>
<td>50.0</td>
<td>34.0</td>
<td>163.0</td>
<td>54.333333</td>
</tr>
<tr>
<th>11</th>
<td>11</td>
<td>1220131</td>
<td>KANI</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>96.0</td>
<td>95.0</td>
<td>96.0</td>
<td>96.0</td>
<td>383.0</td>
<td>127.666667</td>
</tr>
<tr>
<th>12</th>
<td>12</td>
<td>1220132</td>
<td>LATHESSH</td>
<td>1999-03-05</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>0.0</td>
<td>68.0</td>
<td>70.0</td>
<td>70.0</td>
<td>208.0</td>
<td>69.333333</td>
</tr>
<tr>
<th>13</th>
<td>13</td>
<td>1220133</td>
<td>MANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>71.0</td>
<td>76.0</td>
<td>0.0</td>
<td>71.0</td>
<td>0.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>14</th>
<td>14</td>
<td>1220134</td>
<td>NANI</td>
<td>20001109</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>79.0</td>
<td>77.0</td>
<td>80.0</td>
<td>79.0</td>
<td>315.0</td>
<td>105.000000</td>
</tr>
<tr>
<th>15</th>
<td>15</td>
<td>1220135</td>
<td>0</td>
<td>19990125</td>
<td>0</td>
<td>0</td>
<td>0.0</td>
<td>0.0</td>
<td>0.0</td>
<td>0.0</td>
<td>0.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>16</th>
<td>16</td>
<td>1220136</td>
<td>PRATHAP</td>
<td>20000921</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>86.0</td>
<td>84.0</td>
<td>90.0</td>
<td>86.0</td>
<td>346.0</td>
<td>115.333333</td>
</tr>
<tr>
<th>17</th>
<td>17</td>
<td>1220137</td>
<td>RAGHU</td>
<td>20001109</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>67.0</td>
<td>64.0</td>
<td>70.0</td>
<td>0.0</td>
<td>201.0</td>
<td>67.000000</td>
</tr>
<tr>
<th>18</th>
<td>18</td>
<td>1220138</td>
<td>RATHI</td>
<td>20001121</td>
<td>FEMALE</td>
<td>KANCHIPURAM</td>
<td>81.0</td>
<td>86.0</td>
<td>90.0</td>
<td>81.0</td>
<td>338.0</td>
<td>112.666667</td>
</tr>
<tr>
<th>19</th>
<td>19</td>
<td>1220139</td>
<td>SARVESH</td>
<td>19990305</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>84.0</td>
<td>87.0</td>
<td>0.0</td>
<td>84.0</td>
<td>0.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>20</th>
<td>20</td>
<td>1220140</td>
<td>SANTHOSH</td>
<td>20001002</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>76.0</td>
<td>69.0</td>
<td>80.0</td>
<td>76.0</td>
<td>301.0</td>
<td>100.333333</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-cdbb56f9-58d5-44b1-86c3-cd7ce0e919a0')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.dtypes
```




<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>0</th>
</tr>
</thead>
<tbody>
<tr>
<th>sepal_length</th>
<td>float64</td>
</tr>
<tr>
<th>sepal_width</th>
<td>float64</td>
</tr>
<tr>
<th>petal_length</th>
<td>float64</td>
</tr>
<tr>
<th>petal_width</th>
<td>float64</td>
</tr>
<tr>
<th>species</th>
<td>object</td>
</tr>
</tbody>
</table>
</div><br><label><b>dtype:</b> object</label>




```python
df.fillna(method='ffill') #forward fill
```

/tmp/ipython-input-1943891123.py:1: FutureWarning: DataFrame.fillna with 'method' is deprecated and will raise in a future version. Use obj.ffill() or obj.bfill() instead.
df.fillna(method='ffill') #forward fill






<div id="df-f852ab58-dd8e-458c-a1c8-7c5e2f3bf39a" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>1</td>
<td>1220121</td>
<td>ARUN</td>
<td>2000-02-10</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>82.0</td>
<td>81.0</td>
<td>90.0</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
</tr>
<tr>
<th>1</th>
<td>2</td>
<td>1220122</td>
<td>BABU</td>
<td>1999-01-25</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>56.0</td>
<td>61.0</td>
<td>80.0</td>
<td>56.0</td>
<td>253.0</td>
<td>84.333333</td>
</tr>
<tr>
<th>2</th>
<td>3</td>
<td>1220123</td>
<td>CHARAN</td>
<td>2000.09.21</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>56.0</td>
<td>59.0</td>
<td>60.0</td>
<td>70.0</td>
<td>253.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>3</th>
<td>4</td>
<td>1220124</td>
<td>DEVA</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>74.0</td>
<td>79.0</td>
<td>80.0</td>
<td>74.0</td>
<td>307.0</td>
<td>102.333333</td>
</tr>
<tr>
<th>4</th>
<td>5</td>
<td>1220125</td>
<td>ESTER</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>92.0</td>
<td>95.0</td>
<td>96.0</td>
<td>92.0</td>
<td>375.0</td>
<td>125.000000</td>
</tr>
<tr>
<th>5</th>
<td>6</td>
<td>1220126</td>
<td>FARHANA</td>
<td>1999-03-05</td>
<td>FEMALE</td>
<td>THANDALAM</td>
<td>91.0</td>
<td>88.0</td>
<td>90.0</td>
<td>91.0</td>
<td>360.0</td>
<td>120.000000</td>
</tr>
<tr>
<th>6</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>1220128</td>
<td>HEMA</td>
<td>1999-01-25</td>
<td>FEMALE</td>
<td>POONAMALEE</td>
<td>95.0</td>
<td>96.0</td>
<td>90.0</td>
<td>95.0</td>
<td>376.0</td>
<td>125.333333</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>1220129</td>
<td>INDRA</td>
<td>2000.09.21</td>
<td>FEMALE</td>
<td>KANCHIPURAM</td>
<td>64.0</td>
<td>96.0</td>
<td>90.0</td>
<td>64.0</td>
<td>376.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>10</th>
<td>10</td>
<td>1220130</td>
<td>JAHITH</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>34.0</td>
<td>45.0</td>
<td>50.0</td>
<td>34.0</td>
<td>163.0</td>
<td>54.333333</td>
</tr>
<tr>
<th>11</th>
<td>11</td>
<td>1220131</td>
<td>KANI</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>96.0</td>
<td>95.0</td>
<td>96.0</td>
<td>96.0</td>
<td>383.0</td>
<td>127.666667</td>
</tr>
<tr>
<th>12</th>
<td>12</td>
<td>1220132</td>
<td>LATHESSH</td>
<td>1999-03-05</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>96.0</td>
<td>68.0</td>
<td>70.0</td>
<td>70.0</td>
<td>208.0</td>
<td>69.333333</td>
</tr>
<tr>
<th>13</th>
<td>13</td>
<td>1220133</td>
<td>MANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>71.0</td>
<td>76.0</td>
<td>70.0</td>
<td>71.0</td>
<td>208.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>14</th>
<td>14</td>
<td>1220134</td>
<td>NANI</td>
<td>20001109</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>79.0</td>
<td>77.0</td>
<td>80.0</td>
<td>79.0</td>
<td>315.0</td>
<td>105.000000</td>
</tr>
<tr>
<th>15</th>
<td>15</td>
<td>1220135</td>
<td>NANI</td>
<td>19990125</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>79.0</td>
<td>77.0</td>
<td>80.0</td>
<td>79.0</td>
<td>0.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>16</th>
<td>16</td>
<td>1220136</td>
<td>PRATHAP</td>
<td>20000921</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>86.0</td>
<td>84.0</td>
<td>90.0</td>
<td>86.0</td>
<td>346.0</td>
<td>115.333333</td>
</tr>
<tr>
<th>17</th>
<td>17</td>
<td>1220137</td>
<td>RAGHU</td>
<td>20001109</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>67.0</td>
<td>64.0</td>
<td>70.0</td>
<td>86.0</td>
<td>201.0</td>
<td>67.000000</td>
</tr>
<tr>
<th>18</th>
<td>18</td>
<td>1220138</td>
<td>RATHI</td>
<td>20001121</td>
<td>FEMALE</td>
<td>KANCHIPURAM</td>
<td>81.0</td>
<td>86.0</td>
<td>90.0</td>
<td>81.0</td>
<td>338.0</td>
<td>112.666667</td>
</tr>
<tr>
<th>19</th>
<td>19</td>
<td>1220139</td>
<td>SARVESH</td>
<td>19990305</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>84.0</td>
<td>87.0</td>
<td>90.0</td>
<td>84.0</td>
<td>338.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>20</th>
<td>20</td>
<td>1220140</td>
<td>SANTHOSH</td>
<td>20001002</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>76.0</td>
<td>69.0</td>
<td>80.0</td>
<td>76.0</td>
<td>301.0</td>
<td>100.333333</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-f852ab58-dd8e-458c-a1c8-7c5e2f3bf39a')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.fillna(method='bfill')
```

/tmp/ipython-input-3675081237.py:1: FutureWarning: DataFrame.fillna with 'method' is deprecated and will raise in a future version. Use obj.ffill() or obj.bfill() instead.
df.fillna(method='bfill')






<div id="df-61c3df72-811c-4e9b-ae10-3be72e65f595" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>1</td>
<td>1220121</td>
<td>ARUN</td>
<td>2000-02-10</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>82.0</td>
<td>81.0</td>
<td>90.0</td>
<td>56.0</td>
<td>253.0</td>
<td>84.333333</td>
</tr>
<tr>
<th>1</th>
<td>2</td>
<td>1220122</td>
<td>BABU</td>
<td>1999-01-25</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>56.0</td>
<td>61.0</td>
<td>80.0</td>
<td>56.0</td>
<td>253.0</td>
<td>84.333333</td>
</tr>
<tr>
<th>2</th>
<td>3</td>
<td>1220123</td>
<td>CHARAN</td>
<td>2000.09.21</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>74.0</td>
<td>59.0</td>
<td>60.0</td>
<td>70.0</td>
<td>307.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>3</th>
<td>4</td>
<td>1220124</td>
<td>DEVA</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>74.0</td>
<td>79.0</td>
<td>80.0</td>
<td>74.0</td>
<td>307.0</td>
<td>102.333333</td>
</tr>
<tr>
<th>4</th>
<td>5</td>
<td>1220125</td>
<td>ESTER</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>92.0</td>
<td>95.0</td>
<td>96.0</td>
<td>92.0</td>
<td>375.0</td>
<td>125.000000</td>
</tr>
<tr>
<th>5</th>
<td>6</td>
<td>1220126</td>
<td>FARHANA</td>
<td>1999-03-05</td>
<td>FEMALE</td>
<td>THANDALAM</td>
<td>91.0</td>
<td>88.0</td>
<td>90.0</td>
<td>91.0</td>
<td>360.0</td>
<td>120.000000</td>
</tr>
<tr>
<th>6</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>1220128</td>
<td>HEMA</td>
<td>1999-01-25</td>
<td>FEMALE</td>
<td>POONAMALEE</td>
<td>95.0</td>
<td>96.0</td>
<td>90.0</td>
<td>95.0</td>
<td>376.0</td>
<td>125.333333</td>
</tr>
<tr>
<th>9</th>
<td>9</td>
<td>1220129</td>
<td>INDRA</td>
<td>2000.09.21</td>
<td>FEMALE</td>
<td>KANCHIPURAM</td>
<td>64.0</td>
<td>45.0</td>
<td>50.0</td>
<td>64.0</td>
<td>163.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>10</th>
<td>10</td>
<td>1220130</td>
<td>JAHITH</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>34.0</td>
<td>45.0</td>
<td>50.0</td>
<td>34.0</td>
<td>163.0</td>
<td>54.333333</td>
</tr>
<tr>
<th>11</th>
<td>11</td>
<td>1220131</td>
<td>KANI</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>96.0</td>
<td>95.0</td>
<td>96.0</td>
<td>96.0</td>
<td>383.0</td>
<td>127.666667</td>
</tr>
<tr>
<th>12</th>
<td>12</td>
<td>1220132</td>
<td>LATHESSH</td>
<td>1999-03-05</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>71.0</td>
<td>68.0</td>
<td>70.0</td>
<td>70.0</td>
<td>208.0</td>
<td>69.333333</td>
</tr>
<tr>
<th>13</th>
<td>13</td>
<td>1220133</td>
<td>MANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>71.0</td>
<td>76.0</td>
<td>80.0</td>
<td>71.0</td>
<td>315.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>14</th>
<td>14</td>
<td>1220134</td>
<td>NANI</td>
<td>20001109</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>79.0</td>
<td>77.0</td>
<td>80.0</td>
<td>79.0</td>
<td>315.0</td>
<td>105.000000</td>
</tr>
<tr>
<th>15</th>
<td>15</td>
<td>1220135</td>
<td>PRATHAP</td>
<td>19990125</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>86.0</td>
<td>84.0</td>
<td>90.0</td>
<td>86.0</td>
<td>0.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>16</th>
<td>16</td>
<td>1220136</td>
<td>PRATHAP</td>
<td>20000921</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>86.0</td>
<td>84.0</td>
<td>90.0</td>
<td>86.0</td>
<td>346.0</td>
<td>115.333333</td>
</tr>
<tr>
<th>17</th>
<td>17</td>
<td>1220137</td>
<td>RAGHU</td>
<td>20001109</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>67.0</td>
<td>64.0</td>
<td>70.0</td>
<td>81.0</td>
<td>201.0</td>
<td>67.000000</td>
</tr>
<tr>
<th>18</th>
<td>18</td>
<td>1220138</td>
<td>RATHI</td>
<td>20001121</td>
<td>FEMALE</td>
<td>KANCHIPURAM</td>
<td>81.0</td>
<td>86.0</td>
<td>90.0</td>
<td>81.0</td>
<td>338.0</td>
<td>112.666667</td>
</tr>
<tr>
<th>19</th>
<td>19</td>
<td>1220139</td>
<td>SARVESH</td>
<td>19990305</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>84.0</td>
<td>87.0</td>
<td>80.0</td>
<td>84.0</td>
<td>301.0</td>
<td>0.000000</td>
</tr>
<tr>
<th>20</th>
<td>20</td>
<td>1220140</td>
<td>SANTHOSH</td>
<td>20001002</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>76.0</td>
<td>69.0</td>
<td>80.0</td>
<td>76.0</td>
<td>301.0</td>
<td>100.333333</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-61c3df72-811c-4e9b-ae10-3be72e65f595')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python
df.dropna()
```





<div id="df-8f0e2844-a89c-483b-8343-4c122610f9a8" class="colab-df-container">
<div>

<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>SNO</th>
<th>REGNO</th>
<th>NAME</th>
<th>DOB</th>
<th>GENDER</th>
<th>ADDRESS</th>
<th>M1</th>
<th>M2</th>
<th>M3</th>
<th>M4</th>
<th>TOTAL</th>
<th>AVG</th>
</tr>
</thead>
<tbody>
<tr>
<th>1</th>
<td>2</td>
<td>1220122</td>
<td>BABU</td>
<td>1999-01-25</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>56.0</td>
<td>61.0</td>
<td>80.0</td>
<td>56.0</td>
<td>253.0</td>
<td>84.333333</td>
</tr>
<tr>
<th>3</th>
<td>4</td>
<td>1220124</td>
<td>DEVA</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>74.0</td>
<td>79.0</td>
<td>80.0</td>
<td>74.0</td>
<td>307.0</td>
<td>102.333333</td>
</tr>
<tr>
<th>4</th>
<td>5</td>
<td>1220125</td>
<td>ESTER</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>92.0</td>
<td>95.0</td>
<td>96.0</td>
<td>92.0</td>
<td>375.0</td>
<td>125.000000</td>
</tr>
<tr>
<th>5</th>
<td>6</td>
<td>1220126</td>
<td>FARHANA</td>
<td>1999-03-05</td>
<td>FEMALE</td>
<td>THANDALAM</td>
<td>91.0</td>
<td>88.0</td>
<td>90.0</td>
<td>91.0</td>
<td>360.0</td>
<td>120.000000</td>
</tr>
<tr>
<th>6</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>7</th>
<td>7</td>
<td>1220127</td>
<td>GANI</td>
<td>2000-10-02</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>49.0</td>
<td>51.0</td>
<td>70.0</td>
<td>49.0</td>
<td>219.0</td>
<td>73.000000</td>
</tr>
<tr>
<th>8</th>
<td>8</td>
<td>1220128</td>
<td>HEMA</td>
<td>1999-01-25</td>
<td>FEMALE</td>
<td>POONAMALEE</td>
<td>95.0</td>
<td>96.0</td>
<td>90.0</td>
<td>95.0</td>
<td>376.0</td>
<td>125.333333</td>
</tr>
<tr>
<th>10</th>
<td>10</td>
<td>1220130</td>
<td>JAHITH</td>
<td>2000-11-09</td>
<td>MALE</td>
<td>THANDALAM</td>
<td>34.0</td>
<td>45.0</td>
<td>50.0</td>
<td>34.0</td>
<td>163.0</td>
<td>54.333333</td>
</tr>
<tr>
<th>11</th>
<td>11</td>
<td>1220131</td>
<td>KANI</td>
<td>2000-11-21</td>
<td>FEMALE</td>
<td>CHITHUR</td>
<td>96.0</td>
<td>95.0</td>
<td>96.0</td>
<td>96.0</td>
<td>383.0</td>
<td>127.666667</td>
</tr>
<tr>
<th>14</th>
<td>14</td>
<td>1220134</td>
<td>NANI</td>
<td>20001109</td>
<td>MALE</td>
<td>POONAMALEE</td>
<td>79.0</td>
<td>77.0</td>
<td>80.0</td>
<td>79.0</td>
<td>315.0</td>
<td>105.000000</td>
</tr>
<tr>
<th>16</th>
<td>16</td>
<td>1220136</td>
<td>PRATHAP</td>
<td>20000921</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>86.0</td>
<td>84.0</td>
<td>90.0</td>
<td>86.0</td>
<td>346.0</td>
<td>115.333333</td>
</tr>
<tr>
<th>18</th>
<td>18</td>
<td>1220138</td>
<td>RATHI</td>
<td>20001121</td>
<td>FEMALE</td>
<td>KANCHIPURAM</td>
<td>81.0</td>
<td>86.0</td>
<td>90.0</td>
<td>81.0</td>
<td>338.0</td>
<td>112.666667</td>
</tr>
<tr>
<th>20</th>
<td>20</td>
<td>1220140</td>
<td>SANTHOSH</td>
<td>20001002</td>
<td>MALE</td>
<td>KANCHIPURAM</td>
<td>76.0</td>
<td>69.0</td>
<td>80.0</td>
<td>76.0</td>
<td>301.0</td>
<td>100.333333</td>
</tr>
</tbody>
</table>
</div>
<div class="colab-df-buttons">

<div class="colab-df-container">
<button class="colab-df-convert" onclick="convertToInteractive('df-8f0e2844-a89c-483b-8343-4c122610f9a8')"
title="Convert this dataframe to an interactive table."
style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
<path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
</svg>
</button>


</div>


</div>
</div>





```python

```


# Result
          <<include your Result here>>
