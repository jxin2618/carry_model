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
  - [2.1 Augmented Dickey-Fuller unit root tests](#2)
  - [2.2 Ordinary Leasr Square Regression](#2)
  - [2.3 Error Correction Models](#2)
   - [2.3.1 Engle Granger Test and Johansen Test](#2)
   - [2.3.2 Results for the B&K Regression Model](#2)
   - [2.3.3 Results for the Vector Error Correction Model](#2)
    - [2.3.3.1 One Cointegrating Vector](#2)
    - [2.3.3.2 Three Cointegrating Vector](#2)
- [3. Comparison of model prediction](#3)

- [I. Overview of Data](#1)
- [II. Backtesting Philosophy](#2)
- [III. Backtesting Results](#3)
- [IV. Return Models](#4)
- [V. Risk Models](#5)
- [VI. Future Work](#6)

### Keywords
Cost of carry model; Vector error correction model; Engle-Grangle test; Johansen test
### File
- carry_model_1204.html: demonstrates thr research results
### DataSet
- CU.xlsx: contains the data of SHFE copper 
  - in four levels: cash price, future price, inventory, interest rate of government bonds.
  - in the historical period of 2009/12/31 - 2020/07/03
  - 
## Project Research
