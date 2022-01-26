# 파이썬 type 에러



> TypeError: 'int' object is not subscriptable



오류 설명 : int형 인덱싱 불가



해결 : 인덱싱 대상이 list가 아닌 int인지 점검



-----------------------------------



> TypeError: import_optional_dependency() got an unexpected keyword argument 'errors'



오류 설명 : pandas 버전이 낮아 발생



해결 : 

```
import pandas as pd
print(pd.__version__)
```

pandas 버전을 확인해보고, 버전이 1.3보다 낮으면 업그레이드

```
!pip install pandas --upgrade
```

참고 : <https://stackoverflow.com/questions/68722609/lda-visualization-import-optional-dependency-got-an-unexpected-keyword-argum>



--------------------------
