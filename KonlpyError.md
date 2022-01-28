# 파이썬 Konlpy 에러



konlpy를 설치하기 위해서는 java 설치가 필요하다. jdk를 설치하고, 환경변수를 사용자 변수에서 이름을 'JAVA_HOME', 값을 'C:\Program Files\Java\jdk-7.0.2\bin'로 설정한다.



<https://www.lfd.uci.edu/~gohlke/pythonlibs/#jpype> 에서 만약 파이썬 버전이 3.9라면 cp39를, 윈도우 64bit이라면 amd64를 설치해준다. 해당 경로의 커맨드를 열어 다음 코드를 이용하여 설치한다.

```
pip install JPype1‑1.3.0‑cp39‑cp39‑win_amd64.whl
```

모두 설치가 끝났다면 다음 코드를 이용하여 konlpy를 설치한다.

```
pip install konlpy
```

\+


konlpy 설치가 올바르게 되었음에도 불구하고 konlpy 코드를 실행하면 아래와 같은 오류가 떴다. 



> jpype._jvmfinder.JVMNotFoundException: No JVM shared library file (jvm.dll) found. Try setting up the JAVA_HOME environment variable properly.



이는 오류창에서 ivm.py 파일로 이동하여 15번 줄 init_jvm 함수 안에 다음 코드를 추가하면 해결된다.


```
jvmpath = "C:\\Program Files\\Java\\jdk-17.0.2\\bin\\server\\jvm.dll"
```


참고 : <https://clsrn4561.tistory.com/1>
