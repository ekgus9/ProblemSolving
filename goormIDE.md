# goorm IDE 사용 중 에러



> OSError: [Errno 98] Address already in use



goorm에서 flask를 사용하여 개발중에 발생한 에러이다. 이는 사용하려는 포트가 비정상적으로 정령당하여 쓸 수 없는 상황에서 발생한다.



해결 : 



- PID 확인

```
$ lsof -i :5000
```

or

```
$ netstat -tnlp
```

- KILL (<PID> 부분에 앞 코드로 확인한 PID를 넣어주면 된다.)

```
$ sudo kill -9 <PID>
```

참고 : <https://joft.site/143>

  
  
---------------
  
  
  
구름에선 셀레니움을 현재 사용할 수 없다고 한다. (크롬 관련 전체를..)
  
  
  
  
