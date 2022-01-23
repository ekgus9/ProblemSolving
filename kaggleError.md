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



+



> 401 - Unauthorized



:

```
! kaggle competitions download -c 대회이름
! kaggle competitions submit -c 대회이름 -f Submission.csv -m "Message"
```

위 코드와 같이 대회 파일을 다운로드 받으려 하거나 파일을 제출할 때 발생한 에러이다. 프로필을 누르면 나오는 account에서 휴대폰 인증을 받아 해결되었다.



---------------------



