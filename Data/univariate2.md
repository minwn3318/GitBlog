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
- sns 방법
    - 데이터 처리가 필요함
```
sns.countplot(x='BMIStatus', data=diabetes)
plt.show()
```
### box plot
**형태**
- 최솟값
- 최댓값
- 25퍼
- 50퍼
- 75퍼
- iqr : 75 - 25 차이
- 이상치 : iqr * 1.5를 넘어가는 비정상적?으로 추정되는 값

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