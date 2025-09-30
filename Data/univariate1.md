# 단변량 - 수치형
---
## 수치화
### 평균
- mean()
```
diabetes['BMI'].mean()
```

### 중앙값
- median()
```
diabetes['BMI'].median()
```

### 최빈값
- mode()
```
diabetes['BMIStatus'].mode()
```

### 사분위수
- Describe()
```
diabetes['BMI'].describe()
```
- 사분위수 원하는 거 나타내기
```
print('Q1:', diabetes['BMI'].describe()['25%'])
print('Q2:', diabetes['BMI'].describe()['50%'])
print('Q3:', diabetes['BMI'].describe()['75%'])
```

### 기술통계 정보
**describe().T : 가로 세로 방향 바꾸어서 보여줌**

---
## 시각화
### 히스토그램
데이터 분포를 확인하는 가장 기본적인 시각화
- plt.hist()
- seaborn.histplot()

### Density Plot
데이터 밀도를 추정하는 시각화
- seaborn.kdeplot()

### Box Plot
데이터 분포를 확인하는 시각화
- seaborn.boxplot()

### 시계열 데이터
