# 20210730

1. DataFrame 인덱싱 2
1>

        iphone_df.loc[['iphone X', 'iphone 8']]
        iphone_df[['Face ID', '출시일', '메모리']]
        iphone_df.loc['iphone 8' : 'iphone XS'] // 슬라이싱
        

        iphone_df.loc[: 'iphone XS']
        iphone_df.loc[:, '메모리' : 'Face ID'] // column으로 슬라이싱하는 건 조금 더 복잡하게 써야 함
                                          // 전체에 대하여 콜럼을 슬라이싱 한다는 뜻.
        iphone_df.loc['iphone 7' : 'iphone X', '메모리' : 'Face ID']
        
#1 방송사 시청률 받아오기 4

      import pandas as pd

      df = pd.read_csv('data/broadcast.csv', index_col=0)

      df.loc[2012 : 2017, 'KBS' : 'SBS']
      
2> DataFrame 조건으로 인덱싱

      iphone_df.loc[[True, False, True, True, False, True, False]] // true인 4개만 프린트됨
      iphone_df.locp[[True, False, False, True]] // 길이가 8인데 index가 4개이면 뒤의 4개는 false로 간주
      
      iphone_df.loc[:, [True, False, False, True]] // column 인덱싱
      
      iphone_df['디스플레이'] > 5 // 5보다 큰지 true/false 알려줌.
      
      iphone_df.loc[iphone_df['디스플레이'] > 5] // 디스플레이가 5보다 큰 애들만 필터링이 됨.
      
      iphone_df['Face ID'] == 'Yes'
      iphone_df.loc[iphone_df['Face ID'] == 'Yes']
 
      condition = (iphone_df['디스플레이'] > 5) & (iphone_df['Face ID'] == 'Yes')
      iphone_df[condition]
      condition2 = (iphone_df['디스플레이'] > 5) | (iphone_df['Face ID'] == 'Yes')
      
#2 방송사 시청률 받아오기 5

      import pandas as pd

      df = pd.read_csv('data/broadcast.csv', index_col=0)
      
      df['KBS'].loc[df['KBS'] > 30]
      df.loc[df['KBS'] > 30, 'KBS'] // 두 줄이 같은 결과
      
      // 1> df의 KBS 슬라이싱 후 row 추출, 2> df의 row, col 동시 추출
      

#3 방송사 시청률 받아오기 6

      import pandas as pd

      df = pd.read_csv('data/broadcast.csv', index_col=0)

      condition = df['SBS'] < df['TV CHOSUN']
      df.loc[condition, ['SBS', 'TV CHOSUN']] // df[['SBS','TV CHOSUN']].loc[condition] 동일
      
      

      
