# pandas 공부
---
## 데이터프레임 만들기
- import pandas as pd : 라이브러리 저장
- DataFrame : 데이터프레임 만들기
- read_csv : csv url 읽기
- inplace 속성 : 데이터 변경 사항을 반환이 아닌 자체에 저장하여 변경
- index_set() : 인덱스를 설정하는 것
- reset_set(drop) : 인덱스 초기화, 드랍은 기존의 인덱스를 삭제할 것인가 결정

---
## 데이터프레임 탐색
### head, info, describe는 거의 핵심
- head(): 상위 데이터 확인
- tail(): 하위 데이터 확인
- shape: 데이터프레임 크기
- index: 인덱스 정보 확인
- values: 값 정보 확인
- columns: 열 정보 확인
- dtypes: 열 자료형 확인
- info(): 열에 대한 상세한 정보 확인
- describe(): 기술통계정보 확인
- unique() : 고윳
- values_counts() : 값 갯수
- sum() : 데이터 합
- mode() : 최빈값
- max() : 최대값
- min() : 최솟값
- mean() : 중간값

---
## 데이터프레임 조회
- .loc[ 행 : 열 ] : 특정 데이터 조회
- .loc[  : 열 ] : 특정  조회, 복수열 조회시 반드시 리스트로 해서 열에 넣기
- .sort_values(by = [], ascending = True/False) : 정렬
- 조건을 넣어 조회도 가능

---
## 데이터프레임 변경
- rename : 열 이름 변경
- df['final_amt'] = df['total_bill'] + df['tip'] : 열 추가(뒤에)
- insert(index, cloumns) : 인덱스에 열 추 
- drop : 열 삭제
- tip['sex'] = tip['sex'].map({'Male': 1, 'Female': 0}) : 범줏값 변경(매칭 안되면 nan)
- tip['sex'] = tip['sex'].replace({'Male': 1, 'Female': 0}) : 범주값 변경 (매칭안되면 그대로 )
- copy : 복사

---
## 결측치 처리
- isna : 결측치가 있으면 true
- notna : 결측치가 없으면 true
- dropna: 결측치 있는 행을 삭제
- ffill: 바로 앞의 값으로 변경(Forward Fill)
- bfill: 바로 다음 값으로 변경(Backward Fill)
- interpolate() : 메서드를 사용해 선형보간법으로 채움

---
## 합치기
### 조건 : 열이 하나라도 같아야 함
- concat : 가로로 붙이기
- merge : 세로로 붙이기 (join)
on은 어떤 열을 기준으로
- **inner은 내부조인(두 테이블에 다 존재)**
- **outter은 외부조인(두 테이블 중 하나에만 있어도 인정함)**
- **left는 왼쪽것만 가져오라는 것**
- **right는 오른쪽것만 가져오라는 것**
