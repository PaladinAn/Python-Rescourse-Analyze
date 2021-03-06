# Python-Rescourse
  -------------------------------------------------
  
  
  Magic儲存指令
    %history -n 1-4
  
  NumPy 
    
    
    查看資料型態 type()   參數放 []  或" "
    np.arrar([, , , , ])  建立陣列   若需要明確設定，dtype ，np.arrar([, , , , ], dtype="float32") 
      3X5 亂數      np.random.random((3, 5))
      3X5 亂數常態  np.random.nornmal((3, 5))
      3X5 亂數整數  np.random.randint((3, 5))
      3X5 亂數整數，範圍[0, 10]  np.random.randint(0, 10, (3, 5))
      3X5 亂數整數，1維  np.random.randint((3, 5), size=6)
      3X5 亂數整數，2維  np.random.randint((3, 5), size=(3, 4)
      3X5 亂數整數，3維  np.random.randint((3, 5), size=(3, 4, 5)
    切片符號 :
      前面5個   X[:5]
      5後面     X[5:]
      間隔2     X[::2]   結果array([0, 2, 4, 6, 8])
      反轉      X[::-1]  結果array([9, 8, 7, 6, 5, 4, 3, 2, 1, 0])
      殂5後面開始反轉間隔2    X[5::-2]     結果array([5, 3, 1])
      
      多維切片  原式     array([12, 5, 6, 7], 
                              [2, 3, 6, 7], 
                              [0, 2, 3, 8])   
      X[:2, :3] 就是，把 2X3 框起來
                        array([12, 5, 6], 
                              [2, 3, 6], 
      X[:3, ::2] 匡3X2，但是後面的2是切第二號位置
                        array([12, 6], 
                              [2, 6], 
                              [0, 3])  
      切第一欄 (直)  print(:, 0)   array([12, 2, 0]
      切第一列 (横)  print(0, :)   array([12, 5, 6, 7]
      
     重塑 reshape()
     把1~9放入3X3     np.arrange(1,10).reshape((3, 3))
                             array[[1, 2, 3]
                                   [4, 5, 6]
                                   [7, 8, 9]]
            x = np.array[1, 2, 3] 透過  reshape(3, 1)
                                        變成3X1
                                            array([1], 
                                                  [2], 
                                                  [3])
     串接  
            np.concatente([])
      X = np.array([1, 2, 3])
      Y = np.array([4, 5, 6])
               np.concatente([X, Y])             =>array([1, 2, 3, 4, 5, 6, 7, 8, 9])
        串2維，  也可以用 .vstack()
          X1 = np.array([1, 2],
                        [3, 4])
               np.concatente([X1, X1])           =>array([1, 2], 
                                                         [3, 4], 
                                                         [1, 2],
                                                         [3, 4])
        水平串， 也可以用 .hstack()
               np.concatente([X1, X1], axis=1)           =>array([1, 2, 1, 2],
                                                                 [3, 4, 3, 4])
                                                                 
      分割
             np.split([])
       X = [1, 2, 3, 99, 99, 4, 5, 6]
             np.split(X, [3, 5])    切第3、第5的節點     =>[1 2 3][99 99][4 5 6]
         切多維
                    array([1, 2],
                          [3, 4], 
                          [1, 2],
                          [3, 4])
               np.split(X, [2])      =>
                                                 [[1, 2],
                                                  [3, 4]] 
                                                 [[1, 2]
                                                  [3, 4]]
      常用函式
        np.sum          加總
        np.prod         乘積
        np.mean         平均值
        np.std          標準差
        np.var          變異量
        np.min          最小值     np.argmin  索引
        np.max          最大值     np.argman  索引
        np.median       中位數
        np.precentile   排名統計
        np.any          任一值，是Ture 或 != 傳Ture
        np.all          所有值，是Ture 或 != 傳Ture
      
      排序
        選擇排序法
          def selection_sort(x):
            for i in range(len(x)):
            swap = i + np.argmin(x[i:])
            (x[i, x[swap]) = (x[swap], x[i])
          x = np.array([2, 1, 3, 4, 6])
          selection_sort(x)                              =>array([1, 2, 3, 4, 6])
         
         或 Big-O
          def bogosort(x):
            while np.any(x[:-1] > x[1:]):
              np.random.shufflie(x)
              return x
            x = np.array([2, 1, 3, 4, 6])
          bogosort(x)                                    =>array([1, 2, 3, 4, 6])
         
         快速排序法   np.sort()
            x = np.array([2, 1, 3, 4, 6])
            np.sort(x)                                  =>array([1, 2, 3, 4, 6])
            
          欄(上下)小到大，排序  axis=0
            rand = np.random.RandomState(42)
               X = rand.randint(0, 10, (4, 6))
               print(X)                     => [[6 3 7 4 6 9]
                                                [2 6 7 4 3 7]
                                                [7 2 5 4 1 7]
                                                [5 1 4 0 9 5]]
                 np.sort(X, axis=0)
                          =>array([2, 1, 4, 0, 1, 5],
                                  [5, 2, 5, 4, 3, 7], 
                                  [6, 3, 7, 4, 6, 7], 
                                  [7, 6, 7, 4, 9, 9]) 
                                  
           列(左右)小到大，排序  axis=1
            rand = np.random.RandomState(42)
               X = rand.randint(0, 10, (4, 6))
               print(X)                     => [[6 3 7 4 6 9]
                                                [2 6 7 4 3 7]
                                                [7 2 5 4 1 7]
                                                [5 1 4 0 9 5]]
                 np.sort(X, axis=1)
                          =>array([3, 4, 6, 6, 7, 9],
                                  [2, 3, 4, 6, 7, 7], 
                                  [1, 2, 4, 5, 7, 7], 
                                  [0 ,1, 4, 5, 5, 9]) 
         ------------------------------------------------                         
  Pandas
    1維 Serise()
        area_dict = {'California': 423967, 'Texas': 695662, 'New York': 141297,
             'Florida': 170312, 'Illinois': 149995}
        area = pd.Series(area_dict)
                                 =>            California    423967
                                               Florida       170312
                                               Illinois      149995
                                               New York      141297
                                               Texas         695662

    2維 DataFrame
        states = pd.DataFrame({'population': population,
                       'area': area})
                                =>            
                                	                    area	population
                                      California  	423967	38332521
                                      Florida	      170312	19552860
                                      Illinois  	  149995	12882135
                                      New York	    141297	19651127
                                      Texas	        695662	26448193
                                      
      .index   取得 標籤
      .cloumns 取得 欄標籤(上面橫排)
      建立，DataFrame
        pd.DataFrame(population, columns=['population'])
                          =>	            population
                              California	38332521
                                 Florida	19552860
                                Illinois	12882135
                                New York	19651127
                                   Texas	26448193
       From a list of dicts 建立
          data = [{'a': i, 'b': 2 * i}
          for i in range(3)]
          pd.DataFrame(data)
                                    	a 	b
                                   0  0   0
                                   1  1   2
                                   2	2 	4
       From a dictionary of Series objects
          pd.DataFrame({"population": population, "area": area})
          
                           	        area	population
                      California	423967	38332521
                         Florida	170312	19552860
                        Illinois	149995	12882135
                        New York	141297	19651127
                           Texas	695662	26448193 
                           
       From 2維 NumPy array
       pd.DataFrame(np.random.rand(3, 2), columns=['foo', 'bar'], index=['a', 'b', 'c'])
                                   
                                     foo  bar
                            a 	0.865257	0.213169
                            b 	0.442759	0.108267
                            c 	0.047110	0.905718
        
        data['a':'c']
        a    0.25
        b    0.50
        c    0.75
        切片
          data[0: 2]
            a    0.25
            b    0.50
        遮罩
          data[(data > 0.3) & (data < 0.8)]
            b    0.50
            c    0.75
        
        DataFrame  1維，看欄位
          data.欄位名稱    =>  data.area
          
                            California    423967
                            Florida       170312
                            Illinois      149995
                            New York      141297
                            Texas         695662
        DataFrame  2維，看欄位，
          用iloc，切出來
                     data.iloc[:3, :2]
                	area	pop
  California	  423967	38332521
  Florida	      170312	19552860
  Illinois	    149995	12882135
          用loc，指名到多少              
                     data.loc[:'Illinois', :'pop']
          	    area    	pop
 California	  423967	38332521
 Florida  	  170312	19552860
 Illinois	    149995	12882135
 
        DataFrame   
          對齊 A B
          A = pd.DataFrame(rng.randint(0, 20, (2, 2)), columns=list('AB'))
          對齊 B A C
          B = pd.DataFrame(rng.randint(0, 10, (3, 3)), columns=list('BAC'))
          
          在缺失值上，填入所有值的平均數
            fill = A.stack().mean()
            A.add(B, fill_value=fill)
          
          處裡缺失值(NaN)    NaN為一個，浮點數值
            # Null 值處理
            isnull(): 產生布林遮罩
           notnull(): 與 isnull()相反的操作
            dropna(): 回傳一個，過濾過，版本的資料
            fillna(): 回傳一個，有被填入，估算缺失值，的資料
            
            偵測空值:
              data = pd.Series([1, np.nan, 'hello', None])
              法1  data.isnull()
              法2  data[data.notnull()]
              
            拋棄空值:
            任何空值
                .dropna()
            移除，欄或行，的空值  axis=1(直的)
                df.dropna(axis='columns')
            移除，欄或行，且全部都空值，才移除      使用參數 how='all'
                df.dropna(axis='columns', how='all')
            指定多少空值才被保留                          thresh=
                df.dropna(axis='rows', thresh=3)
            
            填入空值:
              fillna()
              data.fillna(0)   填入 0  (補0)

#跨年度-Panel資料-階層式
        建立multi-index
          index = pd.MultiIndex.from_tuples(index)
        查看之前的資料
          pop = pop.reindex(index)
          查看  pop[;, 年度]
          
        轉換 年標籤，轉到上方 .unstack()
          pop_df = pop.unstack()
          
        轉回來，             .stack()
          pop_df.stack()
          
        加入新欄位
          pop_df = pd.DataFrame({'total': pop, 'under18': [9267089, 9284094, 4687374, 4318033, 5906301, 6879014]})
          
          
        建立方法2
          df = pd.DataFrame(np.random.rand(4, 2),
                  index=[['a', 'a', 'b', 'b'], [1, 2, 1, 2]],
                  columns=['data1', 'data2'])
                  
           		    data1	data2
         a	1	0.554233	0.356072
            2	0.925244	0.219474
         b	1	0.441759	0.610054
            2	0.171495	0.886688       
            
        加入索引   左邊標籤   index = pd.MultiIndex.from_product()
            index = pd.MultiIndex.from_product([[2013, 2014], [1, 2]],
                                   names=['year', 'visit'])
                                   
        加入欄     上方標籤    columns = pd.MultiIndex.from_product()
            columns = pd.MultiIndex.from_product([['Bob', 'Guido', 'Sue'], ['HR', 'Temp']],
                                     names=['subject', 'type'])
          再建立DF
          data = np.round(np.random.randn(4, 6), 1)
          data[:, ::2] *= 10
          data += 37
          health_data = pd.DataFrame(data, index=index, columns=columns)
        
        ##索引必須經過排序，才能進行，切片 :
            解決方案，運行  sort_index()
                        
        索引的設定與重設   .reset_index()
          #op_flat = pop.reset_index(name='population')
          	state	    year	population
        0	California	2000	33871648
        1	California	2010	37253956
        2	New York	2000	18976457
        3	New York	2010	19378102
        4	Texas	2000	20851820
        5	Texas	2010	25145561
          #pop_flat.set_index(['state', 'year'])      設定索引
	                     population
            state	year	
      California	2000	33871648
                  2010	37253956
         New York	2000	18976457
                  2010	19378102
            Texas	2000	20851820
                  2010	25145561
                  
       Panda 串接   pd.concat([], [])
                  串横的   axis=1 = axis="col"
                  串上下的 axis=0 (預設)
                打法 pd.concat([], axis=0)
                
             避免，串接發生錯誤
                設定  ignore_index=True
                打法 pd.concat([], axis=0, ignore_index=True)
                     display('x', 'y', 'pd.concat([x, y], ignore_index=True)')
                     pd.concat([x, y], ignore_index=True)
                     
                或，改成階層式
                  display('x', 'y', "pd.concat([x, y], keys=['x', 'y'])")
                    pd.concat([x, y], keys=['x', 'y'])
                    
              兩個 DataFrame 串接    pd.concat()，沒有資料會補NA值
                  df5 = make_df('ABC', [1, 2])
                  df6 = make_df('BCD', [3, 4])
                    display('df5', 'df6', 'pd.concat([df5, df6])')
                    
                 pd.concat([df5, df6])
                 
                若要比免NA值，設定參數  , join="inner"  刪除有NA值的部分
                  pd.concat([df5, df6], join='inner')
                  
                  指定刪除欄位   join_axes=[df5.columns]
               
               另類，串接法  .append()    ##不會變更原來的物件
                    df1.append(df2)    把df2串在df1下面
            
            合併資料   pd.merge()：括號內作業        .join() ：把括號內的東西，放到點前面的裡面
             
             一對一： df3 = pd.merge(df1, df2)     pd.merge() 可以辨識關鍵欄位        (一個相同部位)
             多對一： pd.merge(df3, df4)           pd.merge() 有時候會有重複的項目出現 (多個相同部位合併)
             多對多： pd.merge(df1, df5)           pd.merge()
              
              為了，避免錯誤，可以使用，關鍵字 參數  on="上方欄位名稱"
                    打法： pd.merge(df1, df2, on='employee')
                    
                    如果，想捨棄，不必要的欄位， 使用 .drop()
                      打法：pd.merge(df1, df3, left_on="employee", right_on="name").drop('name', axis=1)
              想合併，指定欄位
                pd.merge(df1, df3, left_on="employee", right_on="name")
         
         統計描述： 資料.dropna().describe()
         
          自動重組......切割、套用、合併，綜合運算  .groupby("索引")
                要求欄位，      .groupby("索引") .aggregate(['min', np.median, max])
                      data1	       data2
          min	median	max	min	median	max
      key						
        A  0	1.5	   3	  3	   4.0  	5
        B	 1	2.5    4	  0    3.5  	7
        C	 2	3.5	   5	  3	   6.0	  9
        
        過濾
          def filter_func(x):
              return x['data2'].std() > 4
              
              df.groupby('key').std()
              df.groupby('key').filter(filter_func)
              
       Grouping example  (綜合打法)
       
        decade = 10 * (planets['year'] // 10)
        decade = decade.astype(str) + 's'
        decade.name = 'decade'
        planets.groupby(['method', decade])['number'].sum().unstack().fillna(0)
        
        titanic.groupby(['sex', 'class'])['survived'].aggregate('mean').unstack()
        
        樞紐分析   
                資料 .pivot_table('survived', index='sex', columns='class')
                                   整個表數據    欄位名稱     欄位
        多層的樞紐分析 
                age = pd.cut(titanic['age'], [0, 18, 80])
                titanic.pivot_table('survived', ['sex', age], 'class')
                                    整個表數據    欄位名稱     欄位
        時間做索引
          index = pd.DatetimeIndex(['2014-07-04', '2014-08-04', '2015-07-04', '2015-08-04'])
          data = pd.Series([0, 1, 2, 3], index=index)
          
          時間系列，資料結構
                   pd.to_datetime()
                   dates = pd.to_datetime([datetime(2015, 7, 3), '4th of July, 2015', '2015-Jul-6', '07-07-2015', '20150708'])
          
           規律時間 pd.date_range()
              打法 pd.date_range('2015-07-03', '2015-07-10')   會給7/3~7/10
                    pd.date_range('2015-07-03', periods=8)
                  
