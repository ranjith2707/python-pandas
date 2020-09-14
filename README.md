# python-pandas
pandas
import numpy as np
import pandas as pd


#series


s =pd.Series([1,2,3,4,5,6,np.nan,8,9,10])
s




#date_range


d =pd.date_range('20200301',periods=10)
d

#DataFrame

df=pd.DataFrame(np.random.randn(10,4),index=d,columns=['A',"B",'C','D'])
df

#DataFrame in dictionary


df1=pd.DataFrame({'A':[1,2,3,4],
                  'B':pd.Timestamp('20200301'),
                  'C':pd.Series(1,index=list(range(4)),dtype='float32'),
                  'D':pd.np.array([5]*4,dtype='int32'),
                  'E':pd.Categorical(['true','False','True','False']),
                  'F':'Ranjith'
                 })

df1

df1.dtypes

# view Data _______________________

df.head()


df.tail()

df.index

df.columns

df.to_numpy()

df.describe()


df.sort_index(axis=1,ascending=False)

df.sort_values(by='C')

df['C']

df[0:3]

df.loc[d[0]]

df.loc[:,['A','C']]

# slicing __________+ using location


df.loc['20200301':'20200306',['D','C']]

df.loc['20200306',['D','C']]

df.loc[d[0],['D','C']]

df.at[d[0],'C']

df.iloc[3]

df.iloc[3:5]

df.iloc[3:5,0:2]

df[df['A']>0]

# Handle Missing Data

df2=df.reindex(index=d[0:4],columns=list(df.columns)+['E'])
df2.loc[d[0]:d[1],'E']=1
df2

df2.isnull()

df2.isnull().count()

df2.dropna()

df2.fillna(value=2)

pd.isna(df2)

# Pandas operations

df.mean()

df.mean(1)

s= pd.Series([1,2,3,np.nan,4,5,6,7,8,9],index=d).shift(2)
s

df.sub(s,axis='index')

df.apply(np.cumsum)

df.apply(lambda X:X.max()- X.min())

s.value_counts()

pd.Series(['edureka','Python','juptyer',np.nan,'football','world'])

# Merging


df =pd.DataFrame(np.random.randn(10,4))
df

df2=[df[:3],df[3:7],df[7:]]
df2

pd.concat(df2)

left =pd.DataFrame({'A':[1,2],'B':[3,4]})
right=pd.DataFrame({'C':[3,2],'D':[4,5]})

left,right

#pd.merge(left,right,on="A") # s.str.upper()

df.groupby(2).sum()

df.groupby([2,3]).sum()

# Group , Reshape

my_tuple=list(zip(*[[1,2,3,4,5,17,18,19],[11,12,13,6,7,8,9,10]]))
index=pd.MultiIndex.from_tuples(my_tuple,names=['First','Second'])
df=pd.DataFrame(np.random.randn(8,2),index=index,columns=['A','B'])
df2=df[:4]
df2.stack(),df2.unstack()

df=pd.DataFrame({
    'A':['a','b','c','d']*3,
    'B':['A','B','C']*4,
    'C':['p','p','p','q','q','q']*2,
    'D':np.random.randn(12),
    'E':np.random.randn(12)
})
pd.pivot_table(df,values='D',index=['A','B'],columns=['C'])

# time series and categorical Data


dates=pd.date_range('3/3/2020',periods=100,freq='S')
ts=pd.Series(np.random.randint(0,500,len(dates)),dates)
ts.resample('5min').sum()

                    

dates =  pd.date_range('3/3/2020 ', periods= 5 , freq='S')
ts = pd.Series(np.random.randn(len(dates)),dates)
ts_utc=ts.tz_localize('UTC')
ts_utc

ts_utc.tz_convert('US/Eastern')

dates =pd.date_range('3/3/2020',periods=5,freq='M')
fs=pd.Series(np.random.randn(len(dates)),dates)
ps=ts.to_period()
ps


ps.to_timestamp()

df =pd.DataFrame({'id':[1,2,3,4,5,6],
                 'grade':['a','b','c','d','e','F']})
df

df['Grade']=df['grade'].astype('category')
df['Grade']
df['Grade']

df['Grade']=df['grade'].astype('category')
df['Grade'].cat.categories=['good','very bad','very good','excellent','d','e']
df['Grade']=df['Grade'].cat.set_categories(['very good','very bad','good','medium','f','h'])
df['Grade']

# data visualization

import matplotlib .pyplot as plt
plt.close('all')
ts=pd.Series(np.random.rand(500),index=pd.date_range('1/2/2020',periods=500))
fs=ts.cumsum()
fs.plot()

# plotting with pandas






