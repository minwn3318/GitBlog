# seabborn 라이브러리
## 환경 준비
```
# 한글 표시를 위해 설치
!pip install koreanize_matplotlib -q
```

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import koreanize_matplotlib
import seaborn as sns
import warnings

warnings.filterwarnings(action='ignore')
%config InlineBackend.figure_format='retina'
```
---
## 기본 그래프
### Histogram
 -histplot() : 단일 열의 데이터 분포를 Histogram으로 표시.
 ```
sns.histplot(x='GRE', data=admission, bins=16, ec='k')
plt.show()
```
- hue 매개변수를 사용하여 구분 기준이 되는 범주형 열을 지정.
```
sns.histplot(x='GRE', hue='ADMIT', data=admission, bins=16, ec='k')
plt.show()
```

### Density Plot
- kdeplot() : 단일 열 또는 두 열의 데이터 분포를 Density Plot으로 표시
    - 숫자형 열의 값 분포를 확인할 수 있는 **커널밀도추정(KDE, Kernel Density Estimation)** 그래프를 표시합니다.
    - 그래프 아래의 면적이 1이 됩니다.
    - x와 y 매개변수중 하나를 사용하여 열을 지정해 표시되는 방향을 조정합니다.
    - hue 매개변수를 사용하여 구분 기준이 되는 범주형 열을 지정할 수 있습니다.
    - 해당 시각화에서는 표준 데이터들과 다르게 튀어나온 이상한 값으로 추정되는 이상값이 0으로 표시됨