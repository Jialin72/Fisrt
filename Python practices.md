# Python 练习题来自小甲鱼以及其他作者
* 练习是根据需求展开,而不是根据教学步骤展开.因此内容安排并不是一个系统的,而是分块的,有目的性的.
# 1 DataFrame
## 1.1 Pandas_DataFrame 基础知识
以下内容来自[Pandas_DataFrame 基础知识](https://www.jianshu.com/p/8024ceef4fe2). 这主要是理解pandas的DataFrame的函数,因为DataFrame是我最常用的数据表.
### 1.1.1 Pandas DataFrame 创建
*DataFrame 的创建主要有两种(对我目前来看):一是根据dict来创建,二是根据读取csv,txt来创建*
  > 根据字典创建
`import pandas as pd
#DataFrame 创建方式主要是根据dict创建及读取csv或者txt文件创建
data={
      'state':['Ohio','Ohio','Ohio','Nevada','Nevada'],
      'year':[2000,20001,2001,2001,2002],
      'pop':[1.5,1.7,3.6,2.4,2.9]
      }
#根据dicth创建DataFrame
frame=pd.DataFrame(data)
frame 
`
`Out: 
    state   year  pop
0    Ohio   2000  1.5
1    Ohio  20001  1.7
2    Ohio   2001  3.6
3  Nevada   2001  2.4
4  Nevada   2002  2.9`
*注 DataFrame在创建过程中可以用pd.DataFrame()函数指定更多参数.比如指定行索引号index;或者列索引号columns*
` frame2=pd.DataFrame(data,index=['one','two','three','four','five'],columns=['year','state','pop','debt']) 

frame2
Out[38]: 
        year   state  pop debt
one     2000    Ohio  1.5  NaN
two    20001    Ohio  1.7  NaN
three   2001    Ohio  3.6  NaN
four    2001  Nevada  2.4  NaN
five    2002  Nevada  2.9  NaN`
*注 我们可以用index，columns，values来访问DataFrame的行索引，列索引以及数据值，数据值返回的是一个二维的ndarray*
`frame2.values
Out[42]: 
array([[2000, 'Ohio', 1.5, nan],
       [20001, 'Ohio', 1.7, nan],
       [2001, 'Ohio', 3.6, nan],
       [2001, 'Nevada', 2.4, nan],
       [2002, 'Nevada', 2.9, nan]], dtype=object)`
输出的就是一个二维数组,没有列索引号和变量名(Data Frame)

  > 读取文件CSV创建  
 读取文件生成DataFrame最常用的是read_csv,read_table方法。例子来自[Pandas_DataFrame loading to networkX](https://github.com/Jialin72/Applied-Social-Network-Analysis-in-Python-University-of-Michigan/blob/master/Module%201/Lecture%20Practice/Loading%20Graphs%20in%20NetworkX/Loading%2BGraphs%2Bin%2BNetworkX.md)
 比如我现在有一个txt文件,如下
 0 1 4
0 2 3
0 3 2
0 5 6
1 3 2
1 6 5
3 4 3
4 5 1
4 7 2
5 8 6
8 9 1
 所使用的函数是`pd.read_csv()`
 `G_df = pd.read_csv('G_edgelist.txt', delim_whitespace=True, 
                   header=None, names=['n1', 'n2', 'weight'])`
` Out[44]: 
    n1  n2  weight
0    0   1       4
1    0   2       3
2    0   3       2
3    0   5       6
4    1   3       2
5    1   6       5
6    3   4       3
7    4   5       1
8    4   7       2
9    5   8       6
10   8   9       1`
这就将文件对入python,为DataFrame格式,然后,用networkX([from_pandas_edgelist()](https://vimsky.com/examples/detail/python-method-networkx.from_pandas_edgelist.html))对DataFrame文件进行画图,以及measurement.

 ### 1.1.2 Pandas DataFrame 性质
 *索引:根据变量名索引*
 `frame2['year']'
 (其他略),总之DataFrame提供了多种形式的索引方式,比如条件索引,修改等
 *将函数应用到各列或者行所形成的一维数组上.*
 >首先介绍的是apply()方法  
>然后是map()方法
 (略)详见[Pandas.DataFrame] https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.apply.html
 *DataFrame中的实现了sum、mean、max等方法
 
