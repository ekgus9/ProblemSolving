# Kill Defunct process 
### 좀비 죽이기



terminal에서 'ps' 명령어로 프로세스 현황을 보면 'kill -9 <PID>'를 해도 죽지 않는 프로세스가 있는 경우가 있다.
  
  
  
- defunct 찾기
  
  
  
```
ps -ef | grep defunct | grep -v grep
```
  
  
  
- 부모 프로세스 확인
  
  
  
```
ps -ef | grep <PID> | grep -v grep
```
  
  
  
부모 프로세스를 죽이면 자동으로 defunct 프로세스도 죽는다. 
  
  

참조 : <http://www.digistory.co.kr/?p=482>
  
  
  
 
