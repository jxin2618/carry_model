# The Cost of Carry Model
Author: Xin Jing

Date: 2021/11/16

This is a replication of a thesis. The title of the thesis is [Does knowledge of the cost of a carry model improve commodity futures price for forecasting ability?](https://github.com/jxin2618/carry_model/blob/main/!Does%20knowledge%20of%20the%20cost%20of%20carry%20model%20improve%20commodity%20futures%20price%20forecasting%20ability%20A%20case%20study%20using%20the%20London%20Metal%20Exchange%20lead%20contract.pdf)

The thesis is a case study on the importance of the **cost of carry model** as well as the future prices in forecasting cash prices. The case study in the thesis uses the London Metal Exchange Lead Contract, while I use Shanghai Futures Exchange copper contract in my research following the pipeline.

## Project Introduction

### Table of Contents
- [1. Data](#1)
  - [1.1 Descriptive statistics](#1-1)
  - [1.2 Graphs](#1-2)
  - [1.3 Auto-Correlation coefficients](#1-3)
- [2. Statistical Tests](#2)
  - [2.1 Ordinary Least Square Regression](#2-1)
    - [Augmented Dickey-Fuller unit root tests](#2-1-1)
    - [**Results for OLS**](#2-1-2)
  - [2.2 Error Correction Models](#2)
    - [Engle Granger Test and Johansen Test](#2-2-1)
    - [**Results for the B&K Regression Model**](#2-2-2)
    - [**Results for the Vector Error Correction Model**](#2-2-3)
      - [One Cointegrating Vector](#2-2-3-1)
      - [Three Cointegrating Vector](#2-2-3-2)
- [3. Comparison of model prediction](#3)
  
### Keywords
Cost of carry model; Brenner and Kroner Model; Error correction model; Engle-Grangle test; Johansen test
### File
- carry_model_1204.html: demonstrates the research results
### DataSet
- CU.xlsx: contains the data of SHFE copper 
  - in four levels: cash price, future price, inventory, interest rate of government bonds.
  - in the historical period of 2009/12/31 - 2020/07/03

### Models
The thesis introduces five models to predict cash price. Two simple models involve only the lagged futures price, as shown in equations $(1)-(2)$. Brenner and Kroner suggested a more complexed model in 1995, as shown in equation $(3)$. Single equation models impose substantial restrictions on the data and so to assess the accuracy of these restrictions a vector error correction model is proposed, see equation $(4)$
- OLS:  
$$ DP_t = a_0 + a_1 DF_{t|t-1} + e_t \tag{1} $$
$$ DP_t = b_0 + b_1 (F_{t|t-1} - P_{t-1}) + e_t \tag{2} $$
- Brenner and Kroner Model(1995):  
$$ DP_t = g_0 + g_1 DF_{t|t-1} + g_2 Dr_{t|t-1} + g_3 DI_{t-1} + g_4 D\sigma_{t-1} + g_5 D\rho_{t-1} + g_6ECT_{t-2} + e_t \tag{3} $$

The error correction term, $ECT_{t-2}$ is the residual, $e_{t-1}$ from the regression:
$$ P_{t-1} = h_0 + h_1 F_{t-1|t-2} + h_2 r_{t-1|t-2} + h_3I_{t-2} + h_4 \sigma_{t-2} + h_5\rho_{t-2} + e_{t-1} $$

- Vector Error Correction Model:
$$ DX_t =  M_1 DX_{t-1} + S^{'}ECT_{t-2}^{*} + L + E_t \tag{4} $$

$DX_t$ is the change in vector $X$, $M_1$ is the matrix of parameters, $S$ is the vector of speed of adjustment parameters, $L$ is a vector of constant terms and $E_t$ is the vector of residuals.$ECT^{*}_{t-2}$ consists of the residuals, $e_t$ based the following regression. 

$$ P_{t-2} = j_0 + j_1 F_{t-1|t-2} + j_2 r_{t-1|t-2} + j_3 I_{t-2} + j_4 \sigma_{t-2} + j_5\rho_{t-2} + e_{t-1} $$

with $i_i$ and $j_i$ as estimated parameters.

Since the jonhansen test in the system indentifies **3 cointegrating vectors** at **5% significance level**, we considered the vector error correction model with one cointegrating vector and three cointegrating vector simultaneously. The simple one cointegrating vector model contrains the error correction term to the cost of carry relationship. This simple version provides a base case for comparison with the more complex three cointegrating vectors model.

## Research Results
The following picture shows the forecasting accuracy with regards to **the difference of the logarithm of cash prices**. The model used in this comparison include the two variable OLS models **(OLS-1 and OLS-2)**, the single equation of the Brenner and Kroner model**(B&K)** and two versions of the vector correction models, the first using one cointegrating vector obtained from the Engle-Granger test **(VECM-1CV)** and second using three cointegrating vectors obtained from the Johansen procedure **(VECM-3CV)**.  

The forecast accuracy is measured in terms of mean error, mean absolute error and mean squared error. The error is defined as actual change in log cash price less the predicted change in log cash price.

The vector error correction model with one cointegrating vector generally shows least bias, while the Brenner & Kroner model exhibits least mean absolute error and least mean squared error.

![image](https://github.com/jxin2618/carry_model/blob/main/figs/AB.png)
![image](https://github.com/jxin2618/carry_model/blob/main/figs/CD.png)

For details, see the file carry_model_1204.html

## Future Work
The advancement in measuring the cash prices can be applied to calibrate the basis rate factors.
