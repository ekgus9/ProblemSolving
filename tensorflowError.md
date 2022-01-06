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



-------------

> could not load dynamic library 'cudart64_110.dll'; dlerror: cudart64_110.dll not found



정상 설치 이후 코드가 실행은 되지만 위 에러가 발생하였다.



이는 CuDA 최신 버전 다운로드로 해결되었다. 



참고: <https://sheepone.tistory.com/126>

-------------

tensorflow는 2.0으로 업데이트 되면서 Session과 placeholder가 사라졌다. 



따라서 두 기능을 사용하면 에러가 발생한다.



> AttributeError: module 'tensorflow' has no attribute 'Session'



> AttributeError: module 'tensorflow' has no attribute 'placeholder'



그러므로 아래 코드는 추가할 필요가 없다.

```
sess = tf.Session()
sess.run()
```
