# Impute missing values in time series through statistical methods

* Processed file: [C:/JLGC/R.LTWB/.datasets/IDEAM_Outlier/Outlier_IQR_Cap_Pivot_EV_TT_D.csv](../IDEAM_Outlier/Outlier_IQR_Cap_Pivot_EV_TT_D.csv)
* Execution date: 2023-09-23 11:06:15.317886
* Python version: 3.11.5 (tags/v3.11.5:cce6ba9, Aug 24 2023, 14:38:34) [MSC v.1936 64 bit (AMD64)]
* Python path: ['C:\\JLGC\\R.LTWB\\.src', 'C:\\Python311\\python311.zip', 'C:\\Python311\\DLLs', 'C:\\Python311\\Lib', 'C:\\Python311']
* matplotlib version: 3.6.0
* pandas version: 2.1.0
* numpy version: 1.25.2
* missingno version: 0.5.2
* sklearn version: 1.3.0
* Stations exclude: ['21185040', '21190110', '21190170', '21190360', '21190430', '21190440', '21190450', '21195080', '21200040', '21200170', '21200390', '21200440', '21200500', '21200580', '21200590', '21200610', '21200650', '21200660', '21200700', '21200710', '21200720', '21200800', '21200830', '21201090', '21201130', '21201150', '21201290', '21201380', '21201620', '21201670', '21201680', '21201690', '21201700', '21201720', '21201730', '21201740', '21201750', '21201760', '21201780', '21201790', '21201810', '21201820', '21201830', '21201840', '21201870', '21202100', '21205012', '21205090', '21205300', '21205340', '21205360', '21205370', '21205450', '21205470', '21205540', '21205550', '21205580', '21205670', '21205700', '21205750', '21205770', '21205910', '21205970', '21206070', '21206100', '21206160', '21206190', '21206200', '21206230', '21206280', '21206310', '21206350', '21206390', '21206410', '21206460', '21206500', '21206510', '21206550', '21206570', '21206610', '21206620', '21206630', '21206640', '21206660', '21206670', '21206680', '21206700', '21206970', '21230080', '21255080', '21255160', '23010140', '23060040', '23060070', '23060080', '23060130', '23060210', '23060220', '23060250', '23060300', '23060310', '23060320', '23065120', '23065140', '23065150', '23065200', '23125170', '24010330', '24010380', '24010490', '24015380', '35020080', '35020090', '35020370', '35025060', '35035030', '35035040', '35035050', '35060010', '35060280', '35065010', '35067050', '35070160']
* Stations include: ['35070110']
* Print table sample: True
* Instructions & script: https://github.com/rcfdtools/R.LTWB/tree/main/Section03/Impute
* License: https://github.com/rcfdtools/R.LTWB/blob/main/LICENSE.md
* Credits: r.cfdtools@gmail.com


## General dataframe information with 6574 IDEAM records for 7 stations

Dataframe records head sample

| Fecha               |   21195190 |   21206930 |   21206950 |   21206980 |   21206990 |   24015110 |   35035130 |
|:--------------------|-----------:|-----------:|-----------:|-----------:|-----------:|-----------:|-----------:|
| 2004-12-31 00:00:00 |        nan |          0 |        nan |        nan |        nan |        nan |        nan |
| 2005-01-01 00:00:00 |        nan |          0 |        nan |        nan |        nan |        nan |        nan |
| 2005-01-02 00:00:00 |        nan |          0 |        nan |        nan |        nan |        nan |        nan |

Dataframe records tail sample

| Fecha               |   21195190 |   21206930 |   21206950 |   21206980 |   21206990 |   24015110 |   35035130 |
|:--------------------|-----------:|-----------:|-----------:|-----------:|-----------:|-----------:|-----------:|
| 2022-12-28 00:00:00 |        556 |        536 |        nan |          0 |          0 |          0 |        nan |
| 2022-12-29 00:00:00 |        511 |        616 |        nan |          0 |          0 |          0 |        nan |
| 2022-12-30 00:00:00 |        476 |        584 |        nan |          0 |          0 |          0 |        nan |

Datatypes for station and nulls values in the initial file
|       | 21195190   | 21206930   | 21206950   | 21206980   | 21206990   | 24015110   | 35035130   |
|:------|:-----------|:-----------|:-----------|:-----------|:-----------|:-----------|:-----------|
| Dtype | float64    | float64    | float64    | float64    | float64    | float64    | float64    |
| Nulls | 1272       | 0          | 380        | 111        | 33         | 178        | 2570       |

![R.LTWB](Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

![R.LTWB](Missingno_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

<div align="center">

General statistics table - Initial file

</div>


<div align="center">

|          |   count |     mean |     std |   min |   25% |   50% |   75% |      max |
|---------:|--------:|---------:|--------:|------:|------:|------:|------:|---------:|
| 21195190 |    5302 | 221.429  | 446.829 |     0 |     0 |     0 |    78 | 1915     |
| 21206930 |    6574 | 130.541  | 287.193 |     0 |     0 |     0 |   135 | 1572.61  |
| 21206950 |    6194 | 160.363  | 440.671 |     0 |     0 |     0 |    51 | 2607     |
| 21206980 |    6463 |  76.5139 | 275.364 |     0 |     0 |     0 |    19 | 1553.07  |
| 21206990 |    6541 | 178.095  | 368.5   |     0 |     0 |     0 |   171 | 2209     |
| 24015110 |    6396 | 281.441  | 478.338 |     0 |     0 |     0 |   339 | 1968     |
| 35035130 |    4004 | 181.794  | 104.686 |     0 |   155 |   218 |   246 |  876.303 |

</div>



## Method 1 - Imputing with mean values
According to this technique, the missing values are imputed using the mean value in each feature and the serie has been completed filled.

Imputed file: [Impute_Mean_Outlier_IQR_Cap_Pivot_EV_TT_D.csv](Impute_Mean_Outlier_IQR_Cap_Pivot_EV_TT_D.csv)

![R.LTWB](Impute_Mean_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

![R.LTWB](Missingno_Impute_Mean_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

<div align="center">

General statistics table - Imputed file

</div>


<div align="center">

|          |   count |     mean |      std |   min |     25% |     50% |     75% |      max |
|---------:|--------:|---------:|---------:|------:|--------:|--------:|--------:|---------:|
| 21195190 |    6574 | 221.429  | 401.271  |     0 |   0     |   0     | 221.429 | 1915     |
| 21206930 |    6574 | 130.541  | 287.193  |     0 |   0     |   0     | 135     | 1572.61  |
| 21206950 |    6574 | 160.363  | 427.743  |     0 |   0     |   0     | 115     | 2607     |
| 21206980 |    6574 |  76.5139 | 273.029  |     0 |   0     |   0     |  22     | 1553.07  |
| 21206990 |    6574 | 178.095  | 367.573  |     0 |   0     |   0     | 177     | 2209     |
| 24015110 |    6574 | 281.441  | 471.816  |     0 |   0     |   0     | 320.75  | 1968     |
| 35035130 |    6574 | 181.794  |  81.6956 |     0 | 181.794 | 181.794 | 228.75  |  876.303 |

</div>



## Method 2 - Imputing with median values
According to this technique, the missing values are imputed using the median value in each feature and the serie has been completed filled.

Imputed file: [Impute_Median_Outlier_IQR_Cap_Pivot_EV_TT_D.csv](Impute_Median_Outlier_IQR_Cap_Pivot_EV_TT_D.csv)

![R.LTWB](Impute_Median_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

![R.LTWB](Missingno_Impute_Median_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

<div align="center">

General statistics table - Imputed file

</div>


<div align="center">

|          |   count |     mean |      std |   min |   25% |   50% |    75% |      max |
|---------:|--------:|---------:|---------:|------:|------:|------:|-------:|---------:|
| 21195190 |    6574 | 178.585  | 410.696  |     0 |     0 |     0 |   0    | 1915     |
| 21206930 |    6574 | 130.541  | 287.193  |     0 |     0 |     0 | 135    | 1572.61  |
| 21206950 |    6574 | 151.094  | 429.377  |     0 |     0 |     0 |  37    | 2607     |
| 21206980 |    6574 |  75.2219 | 273.207  |     0 |     0 |     0 |  18    | 1553.07  |
| 21206990 |    6574 | 177.201  | 367.789  |     0 |     0 |     0 | 167.75 | 2209     |
| 24015110 |    6574 | 273.821  | 474.023  |     0 |     0 |     0 | 320.75 | 1968     |
| 35035130 |    6574 | 195.948  |  83.5843 |     0 |   206 |   218 | 228.75 |  876.303 |

</div>



## Method 3 - Imputing with Last Observation Carried Forward (LOCF) values
According to this technique, the missing values are imputed using the immediate values before it in the time series and the missing values at the start are not filled but the series are completed fillet to the end.

Imputed file: [Impute_LOCF_Outlier_IQR_Cap_Pivot_EV_TT_D.csv](Impute_LOCF_Outlier_IQR_Cap_Pivot_EV_TT_D.csv)

![R.LTWB](Impute_LOCF_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

![R.LTWB](Missingno_Impute_LOCF_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

<div align="center">

General statistics table - Imputed file

</div>


<div align="center">

|          |   count |     mean |     std |   min |   25% |   50% |   75% |      max |
|---------:|--------:|---------:|--------:|------:|------:|------:|------:|---------:|
| 21195190 |    5302 | 221.429  | 446.829 |     0 |     0 |   0   |    78 | 1915     |
| 21206930 |    6574 | 130.541  | 287.193 |     0 |     0 |   0   |   135 | 1572.61  |
| 21206950 |    6403 | 157.055  | 433.792 |     0 |     0 |   0   |    59 | 2607     |
| 21206980 |    6463 |  76.5139 | 275.364 |     0 |     0 |   0   |    19 | 1553.07  |
| 21206990 |    6541 | 178.095  | 368.5   |     0 |     0 |   0   |   171 | 2209     |
| 24015110 |    6396 | 281.441  | 478.338 |     0 |     0 |   0   |   339 | 1968     |
| 35035130 |    6224 | 128.722  | 110.139 |     0 |    33 | 126.5 |   231 |  876.303 |

</div>



## Method 4 - Imputing with Next Observation Carried Backward (NOCB) values
According to this technique, the missing values are imputed using the immediate values after it in the time series and the missing values at the end are not filled but the series are completed fillet to the start.

Imputed file: [Impute_NOCB_Outlier_IQR_Cap_Pivot_EV_TT_D.csv](Impute_NOCB_Outlier_IQR_Cap_Pivot_EV_TT_D.csv)

![R.LTWB](Impute_NOCB_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

![R.LTWB](Missingno_Impute_NOCB_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

<div align="center">

General statistics table - Imputed file

</div>


<div align="center">

|          |   count |     mean |     std |   min |   25% |   50% |    75% |      max |
|---------:|--------:|---------:|--------:|------:|------:|------:|-------:|---------:|
| 21195190 |    6574 | 226.377  | 401.399 |     0 |     0 |     0 | 247    | 1915     |
| 21206930 |    6574 | 130.541  | 287.193 |     0 |     0 |     0 | 135    | 1572.61  |
| 21206950 |    6365 | 157.103  | 435.153 |     0 |     0 |     0 |  43    | 2607     |
| 21206980 |    6574 |  75.2219 | 273.207 |     0 |     0 |     0 |  18    | 1553.07  |
| 21206990 |    6574 | 177.959  | 367.578 |     0 |     0 |     0 | 167.75 | 2209     |
| 24015110 |    6574 | 279.073  | 472.03  |     0 |     0 |     0 | 320.75 | 1968     |
| 35035130 |    4354 | 172.647  | 105.05  |     0 |    68 |   213 | 244    |  876.303 |

</div>



## Method 5 - Impute missing values with Linear Interpolation values
According to this technique, the missing values are imputed using the linear interpolation between knowing pair values in the time series and the missing values at the start are not filled but the series are completed fillet to the end.

Imputed file: [Impute_InterpolateLinear_Outlier_IQR_Cap_Pivot_EV_TT_D.csv](Impute_InterpolateLinear_Outlier_IQR_Cap_Pivot_EV_TT_D.csv)

![R.LTWB](Impute_InterpolateLinear_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

![R.LTWB](Missingno_Impute_InterpolateLinear_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

<div align="center">

General statistics table - Imputed file

</div>


<div align="center">

|          |   count |     mean |     std |   min |   25% |   50% |   75% |      max |
|---------:|--------:|---------:|--------:|------:|------:|------:|------:|---------:|
| 21195190 |    5302 | 221.429  | 446.829 |     0 |     0 |   0   |    78 | 1915     |
| 21206930 |    6574 | 130.541  | 287.193 |     0 |     0 |   0   |   135 | 1572.61  |
| 21206950 |    6403 | 157.055  | 433.792 |     0 |     0 |   0   |    59 | 2607     |
| 21206980 |    6463 |  76.5139 | 275.364 |     0 |     0 |   0   |    19 | 1553.07  |
| 21206990 |    6541 | 178.095  | 368.5   |     0 |     0 |   0   |   171 | 2209     |
| 24015110 |    6396 | 281.441  | 478.338 |     0 |     0 |   0   |   339 | 1968     |
| 35035130 |    6224 | 128.722  | 110.139 |     0 |    33 | 126.5 |   231 |  876.303 |

</div>



## Method 6 - Impute missing values with Exponential (Weighted) Moving Average - EWM = 3
According to this technique, the missing values are imputed using the moving average values in the time series and the missing values at the start are not filled but the series are completed fillet to the end.

Imputed file: [Impute_MeanEWM_Outlier_IQR_Cap_Pivot_EV_TT_D.csv](Impute_MeanEWM_Outlier_IQR_Cap_Pivot_EV_TT_D.csv)

![R.LTWB](Impute_MeanEWM_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

![R.LTWB](Missingno_Impute_MeanEWM_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

<div align="center">

General statistics table - Imputed file

</div>


<div align="center">

|          |   count |     mean |     std |   min |   25% |   50% |     75% |      max |
|---------:|--------:|---------:|--------:|------:|------:|------:|--------:|---------:|
| 21195190 |    5302 | 221.429  | 446.829 |     0 |     0 |     0 |  78     | 1915     |
| 21206930 |    6574 | 130.541  | 287.193 |     0 |     0 |     0 | 135     | 1572.61  |
| 21206950 |    6403 | 170.042  | 436.609 |     0 |     0 |     0 |  80     | 2607     |
| 21206980 |    6463 |  76.5139 | 275.364 |     0 |     0 |     0 |  19     | 1553.07  |
| 21206990 |    6541 | 178.095  | 368.5   |     0 |     0 |     0 | 171     | 2209     |
| 24015110 |    6396 | 281.441  | 478.338 |     0 |     0 |     0 | 339     | 1968     |
| 35035130 |    6224 | 291.525  | 169.617 |     0 |   202 |   247 | 489.436 |  876.303 |

</div>



## Method 7 - Impute missing values with Natural Neigborns - KNN = 5 Imputer from Scikit Learn
According to this technique, the missing values are imputed using the natural neighbors values and the serie has been completed filled. More information in https://scikit-learn.org/stable/modules/generated/sklearn.impute.KNNImputer.html

Imputer = KNNImputer(n_neighbors=n_neighbors, weights=uniform, metric=nan_euclidean)

Imputed file: [Impute_KNN_Outlier_IQR_Cap_Pivot_EV_TT_D.csv](Impute_KNN_Outlier_IQR_Cap_Pivot_EV_TT_D.csv)

![R.LTWB](Impute_KNN_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

![R.LTWB](Missingno_Impute_KNN_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

<div align="center">

General statistics table - Imputed file

</div>


<div align="center">

|          |   count |     mean |     std |   min |   25% |   50% |    75% |      max |
|---------:|--------:|---------:|--------:|------:|------:|------:|-------:|---------:|
| 21195190 |    6574 | 218.438  | 421.532 |     0 |  0    |   0   | 216    | 1915     |
| 21206930 |    6574 | 130.541  | 287.193 |     0 |  0    |   0   | 135    | 1572.61  |
| 21206950 |    6574 | 158.914  | 433.011 |     0 |  0    |   0   |  55.2  | 2607     |
| 21206980 |    6574 |  75.8315 | 273.17  |     0 |  0    |   0   |  20    | 1553.07  |
| 21206990 |    6574 | 177.339  | 367.76  |     0 |  0    |   0   | 168.75 | 2209     |
| 24015110 |    6574 | 277.195  | 473.037 |     0 |  0    |   0   | 328    | 1968     |
| 35035130 |    6574 | 171.843  | 125.509 |     0 | 88.25 | 202.8 | 237.8  |  876.303 |

</div>



## Method 8 - Impute missing values with Multivariate Imputation by Chained Equation - MICE from Scikit Learn
According to this technique, the missing values are imputed using MICE values and the serie has been completed filled. More information in https://scikit-learn.org/stable/modules/generated/sklearn.impute.IterativeImputer.html

Imputer = IterativeImputer(estimator=BayesianRidge(), min_value=0, n_nearest_features=5)

Imputed file: [Impute_MICE_Outlier_IQR_Cap_Pivot_EV_TT_D.csv](Impute_MICE_Outlier_IQR_Cap_Pivot_EV_TT_D.csv)

![R.LTWB](Impute_MICE_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

![R.LTWB](Missingno_Impute_MICE_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.png)

<div align="center">

General statistics table - Imputed file

</div>


<div align="center">

|          |   count |     mean |      std |   min |   25% |   50% |     75% |      max |
|---------:|--------:|---------:|---------:|------:|------:|------:|--------:|---------:|
| 21195190 |    6574 | 195.798  | 405.756  |     0 |     0 |     0 | 110.237 | 1915     |
| 21206930 |    6574 | 130.541  | 287.193  |     0 |     0 |     0 | 135     | 1572.61  |
| 21206950 |    6574 | 157.184  | 428.178  |     0 |     0 |     0 |  87     | 2607     |
| 21206980 |    6574 |  75.8628 | 273.102  |     0 |     0 |     0 |  20     | 1553.07  |
| 21206990 |    6574 | 178.007  | 367.576  |     0 |     0 |     0 | 169.75  | 2209     |
| 24015110 |    6574 | 279.072  | 472.151  |     0 |     0 |     0 | 325.75  | 1968     |
| 35035130 |    6574 | 201.581  |  94.5959 |     0 |   177 |   218 | 248     |  876.303 |

</div>


Complementary report with individual graphs for stations in [Impute_Station_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.md](Impute_Station_Outlier_IQR_Cap_Pivot_EV_TT_D.csv.md)

> As you notice, some of the techniques showed above can`t fill complete the missing values at the start or at the end, however, you can first choice a method and then apply another complementary method for get full filled the missin values.
