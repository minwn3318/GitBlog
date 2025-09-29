# 데이터 분석 및 시각화
데이터를 분석하는 두 가지 방법
1. 시각화
2. 수치화
---
# matplotlib 라이브러리
파이썬에서 가장 널리 사용되는 시각화 라이브러리 중 하나
- 데이터 시각화를 위한 다양한 종류의 그래프를 생성함
- 데이터 시각화에 필요한 모든 기능을 갖춤

## 기본 세팅
```
import numpy as np //숫자 
import pandas as pd // 데이터프레임
import matplotlib.pyplot as plt //분석 시각화
import seaborn as sns // 시각화 스타일 조절
import koreanize_matplotlib // 글자화
import warnings //주의표시

warnings.filterwarnings(action='ignore') //무시부분 지우기
%config InlineBackend.figure_format='retina' //글자 선명
```

---
## 기본차트 그리기
```
# 데이터 읽어오기
path = 'https://raw.githubusercontent.com/Jangrae/csv/master/stock.csv'
stock = pd.read_csv(path)

# 전처리
stock = stock.loc[stock['Date'].between('2022-12-01', '2022-12-31')]
stock.reset_index(drop=True, inplace=True)
stock.insert(1, 'Day', stock['Date'].str.split('-').str[2]) ## 1째 열에 day추가하는데 데이터 처리를 그리해라
stock.drop('Date', axis=1, inplace=True)

# 확인
stock.head()
```

### 그래프 그리기
- plot : 선형 그래프를 그려줌
    - 값을 하나만 전달하면 이값이 y축
    - 값의 ㅇ위치를 나태니는 인덱스가 x축
- show : 보여주기
```
plt.plot(stock['Close'])
plt.show()
```

###x축, y축의 값 지정하기
- 앞에가 x, 뒤에가 y임
- x와 y의 값이 str이면 생략하지 않고 하나하나 다 보여줌
```
plt.plot(stock['Day'], stock['Close'])
plt.show()
```

- 해당 방법처럼 지정이 가능하며, 이때는 문자열만 해당됨
```
plt.plot('Day', 'Close', data=stock)
plt.show()
```

--- 
## 그래프 꾸미기
### x,y축 이름과 타이틀 지정
- xlabel(), ylabel() : 각 축의 이름을 지정
- title() : 그래프 제목을 지정
```
plt.plot(stock['Day'], stock['Close'])
plt.title('Stock Closing Price', size=15, pad=10)
plt.xlabel('Day')
plt.ylabel('Price')
plt.show()
```

### 선 스타일 설정
<img src='https://raw.githubusercontent.com/jangrae/img/master/style.png' width=600 align="left"/>
- 다음과 같은 속성이 존재함
    - 색깔
    - 마커모양
    - 마커 사이즈
    - 라인 스타일
    - 라인 두께
```
plt.plot(stock['Day'], stock['Close'], 'go--')
plt.title('Stock Closing Price', size=15, pad=10)
plt.xlabel('Day')
plt.ylabel('Price')
plt.show()
```

- 스타일 지정을 다음과 같이 할 수 있음
```
plt.plot(stock['Day'], stock['Open'], color='g', marker='o', linestyle='--')
```

### 여러 그래프 겹쳐서 그리기
- plot를 여러 줄로 중복해서 쓰면 겹쳐서 나옴
    - y값이 비슷할 때는 그냥 그대로 하면 되고, y값이 차이가 나면 조절이 필요하다 
```
plt.plot(stock['Day'], stock['Open'], 'go--')
plt.plot(stock['Day'], stock['Close'], 'rs--')
plt.title('Stock Price', size=15, pad=10)
plt.xlabel('Day')
plt.ylabel('Price')
plt.show()
```

### 범례, 괘선 추가
- legend() : 범례를 표시
    - label() 속성을 사용해 각 그래프의 이름을 지정 후 legend() 함수를 사용
    - 범례 정보를 legend() 함수 안에 리스트 형태로 지정도 가능
- grid() : 괘선 추가
```
plt.plot(stock['Day'], stock['Open'], 'o--', label='Open')
plt.plot(stock['Day'], stock['Close'], 's--', label='Close')
plt.title('Stock Price', size=15, pad=10)
plt.xlabel('Day')
plt.ylabel('Price')
plt.legend()   # loc='upper left' 등으로 위치 변경 가능, default='best'
plt.grid()     # axis 지정 가능 ('both', 'x', 'y')
plt.show()
```
**그래프 저장은 오른쪽 마우스로 복사가 대표사항**

---
## 추가기능
### 축 범위 조정하기
- xlim(최소, 최대), ylim(최소, 최대) : 축에 표시할 범위 지정
```
plt.plot(stock['Day'], stock['Close'], marker='o')
plt.title('Stock Closing Price', size=15, pad=10)
plt.xlabel('Day')
plt.ylabel('Price')
plt.ylim(100, 160)
plt.show()
```

### 그래프 크기 조정
- figuer(가로, 세로): 그래프의 크기 조정
```
plt.figure(figsize=(5, 5))
plt.plot(stock['Day'], stock['Close'], marker='o')
plt.title('Stock Closing Price', size=15, pad=10)
plt.show()
```

### 수평선, 수직선 추가
- axhline(위치, 색, 라인스타일, 라인두께) : 임의 위치에 가로선(y 표시)
- axvline(위치, 색, 라인스타일, 라인두께) : 임의 위치에 세로선(x 표시)
- 위치는 문자열이면 그 갯수로 계산됨, 숫자면 그대로 임

### 텍스트 추가
- text() : 임의 위치에 텍스트를 출력
```
plt.text(-0.5, 135.2, '135', color='r')
plt.text(10.2, 125.5, '10', color='r')

```

### 위, 아래로 그래프 그리기
- subplot(행, 열, 위치) : 여러 행, 열로 그래프르 한번에 표시
- tight_layout() : 그래프가 겹치지 않게 정리
```
plt.subplot(2, 1, 1)
plt.plot(stock['Day'], stock['Open'], color='tab:blue', marker='o')
plt.title('Opening Price')

plt.subplot(2, 1, 2)
plt.plot(stock['Day'], stock['Close'], color='tab:orange', marker='s')
plt.title('Closing Price')

plt.tight_layout()
plt.show()
```

### 옆으로 그래프 그리기
```
plt.subplot(1, 2, 1)
plt.plot(stock['Day'].astype(int), stock['Open'], color='tab:blue', marker='o')
plt.title('Opening Price')

plt.subplot(1, 2, 2)
plt.plot(stock['Day'].astype(int), stock['Close'], color='tab:orange', marker='s')
plt.title('Closing Price')

plt.tight_layout()
plt.show()
```