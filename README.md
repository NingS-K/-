#python清洗数据

import pandas as pd
from pandas import DataFrame

df = pd.read_csv('D:\work\python_pycharm\python_shujufenxi\\05作业数据.csv')
print(type(df))
print(df)

#判断完整性
#1：缺失值补齐
df['ounces'].fillna(df['ounces'].mean(),inplace=True)
print(df)
#2:删除空行
df.dropna(how='all',inplace=True)
print(df)
#唯一性
#1：统一food列小写字母
df['food'] = df['food'].str.lower()
print(df)
#2:ounces列出现负值
df['ounces'] = df['ounces'].apply(lambda a:abs(a))
print(df)
#3:将food下重复的进行合并ounces


df = df.groupby(['food','animal']).mean().reset_index()
print(df)# -
