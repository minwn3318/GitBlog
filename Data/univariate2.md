# 단변량 범주형
---
## 사각화
### Bar plot
- plt 방법
```
temp = diabetes['BMIStatus'].value_counts()

plt.bar(x=temp.index.astype(str), height=temp.values)
plt.show()
```
-sns 방법
```
sns.countplot(x='BMIStatus', data=diabetes)
plt.show()
```
---
### Pie Chart
- plt 방법
    - startangle=90: 90도 부터 시작
    - counterclock=False: 시계 방향으로
    - explode=[0.05, 0.05, 0.05]: 중심으로 부터 1, 2, 3을 얼마만큼 띄울지
    - shadow=True: 그림자 추가
```
temp = diabetes['BMIStatus'].value_counts()

plt.pie(x=temp.values, labels=temp.index, autopct='%.1f%%')
plt.show()
```