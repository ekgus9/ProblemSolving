# Python TensorFlow 설치 Error

```
pip install tensorflow
```

위 코드를 실행 하였을 때 이미 설치가 완료되어 있다고 떠서 설치가 잘된 줄 알았다.



그러나 파이썬에서 import를 하니 tensorflow가 없다고 뜬다. 



conda로 다운로드 받아도 되지 않았다.



리서치해보니 파이썬 버전은 3.7, numpy는 1.17 이하에서 작용을 한다고 한다. 

```
conda install python=3.7
pip install "numpy<1.17" 
```

참고 : <https://jjluveeecom.tistory.com/37>

