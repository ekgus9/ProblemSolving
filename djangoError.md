# Django Errors



### 1. python3 manage.py runserver 무응답

```
>> python3 manage.py runserver 
```

장고를 실행시키기 위해 위 코드를 실행시켰다. 전에는 잘 작동하였는 데 갑자기 "Python"이란 말만 뜨고 응답은 하지 않았다. 아래 코드를 사용하여 정상 실행시킬 수 있었다.

```
python manage.py runserver --noreload
```

장고는 서버를 실행할 경우 2개의 프로세스를 실행하는데, 해당 코드는 한 번만 실행하도록 하는 코드이다. 그러나 라이브 리로드 기능은 사용할 수 없게 된다.



출처: <https://satisfactoryplace.tistory.com/63>, <https://stackoverflow.com/questions/33814615/how-to-avoid-appconfig-ready-method-running-twice-in-django>



### 2. RuntimeError: Model class polls.models.Post doesn't declare an explicit app_label and isn't in an application in INSTALLED_APPS.



apps.py에서



![image](https://user-images.githubusercontent.com/89879599/153887808-6cb3877a-ad41-462c-b8c8-543e556cf6f4.png)



name을 apps이 속한 폴더명으로 명명하면 해결된다.



