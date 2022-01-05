# KAGGLE ERROR



+



> ERROR: Column '' was not expected (Line 1, Column 1)



                                                              
:


제출하기 위해 csv 파일을 생성할 때 생긴 에러로, index=False를 추가하면 해결된다.

```
submission.to_csv('./titanic_submission.csv')
```



   ↓




```
submission.to_csv('./titanic_submission.csv', index = False)
```
---------------------------
