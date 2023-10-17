# Module4
# Initial imports
import pandas as pd
import numpy as np
import datetime as dt
from pathlib import Path

%matplotlib inline

#reading whale returns
whale_data=Path('whale_returns.csv')
whale_df=pd.read_csv(whale_data,index_col='Date')
#count nulls
whale_df.isnull().sum()
#drop nulls
whale_df.dropna(inplace=True)

#reading algorithmic returns
algo_data=Path('algo_returns.csv')
algo_df=pd.read_csv(algo_data,index_col='Date')
#count nulls
algo_df.isnull().sum()
#drop nulls
algo_df.dropna(inplace=True)

#reading S&P 500 closing prices
sp500=Path('sp500_history.csv')
sp500_df=pd.read_csv(sp500, index_col="Date")
#check data types
sp500_df.dtypes
sp500_df

#fix data types
#Removing $ and , to later make column in float format
sp500_df["Close"] = sp500_df["Close"].str.replace("$", "")
sp500_df["Close"] = sp500_df["Close"].str.replace(",", "")
sp500_df["Close"] = sp500_df["Close"].astype("float")
sp500_df.dtypes
sp500_df
