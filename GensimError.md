# Python gensim module 설치 오류


gensim 모듈에서 Word2Vec를 사용하기 위해 다음 코드를 cmd 창에 실행하였다.

```
pip install gensim
```

처음엔 잘되는 듯 하다가 에러가 계속 발생하였다.

***************************

이를 해결하기 위해 gensim을 버전을 지정하여 설치해보았다.

```
pip install gensim==3.4.0
```

버전이 3.8 이상은 아예 이전과 같은 에러가 뜨면서 설치되지 않아서 3.4.0을 설치하였더니 설치는 되었다.

***************************

그러나 Visual Studio Code에서 실행을 시켜보니 importerror가 발생하였다.



>importerror: cannot import name 'mapping' from 'collections'



>importerror: cannot import name 'isgenerator' from partially initialized module 'inspect' (most likely due to a circular import)



>importerror: unable to import required dependencies:



이는 gensim 뿐만 아니라 numpy, requests 등의 모듈에도 등장하였다. 



이를 해결하기 위해 에러 메서지에 등장한 모듈의 코드를 하나하나 살펴보았다.




해당 오류는 token.py라는 파일이 생성되어 있었기 때문에 발생했음을 알 수 있었다. 



다른 모듈에서 token 모듈을 import하려고 하면 token.py 파일이 참조되어서 에러가 발생한 것이다.



따라서 파일의 이름을 바꾸어 importerror를 해결하였다.

**************************************

그러나 gensim 에러가 계속 발생하였다.


```
pip install --upgrade gensim
```

도 안되고, source tar.gz를 다운 받아 zip을 풀고

```
python setup.py install
```

을 실행시켜 보았으나 이 또한 되지 않았다.



참고: <https://pypi.org/project/gensim/>


******************

결국 anaconda를 설치하기로 결심한다.



참고: <https://m.blog.naver.com/jonghong0316/221683053696>



anaconda 설치 과정에도 CondaHTTPError가 발생하였다.



```
libcrypto-1_1-x64.*
libssl-1_1-x64.*
```

파일을 CONDA_PATH\Library\bin에서 CONDA_PATH\DLLs 폴더로 이동시키는 것으로 해결되었다. 



참고: <https://stackoverflow.com/questions/55185945/any-conda-or-pip-operation-give-ssl-error-in-windows-10>



이 외에도 



>error: failed building wheel for gensim



>commandnotfounderror: your shell has not been properly configured to use 'conda activate'.



등의 에러가 나타났지만 다음 코드를 사용하여 설치에 성공하기는 하였다. 

```
conda install -c anaconda gensim
```

다시 실행이 문제였다. 



>runtimeerror: compiled extensions are unavailable.



>modulenotfounderror: no module named 'gensim'



후자는 gensim이 설치도 되었고, module list에도 있지만 계속 떴다.

```
conda list
pip list
```

>gen sim error: command errored out with exit status 1:



가 떴을 때는 pip를 최신 버전으로 업그레이드 하려했지만 이미 최신 버전이었다.



모듈을 모두 초기화도 해봤고 파이썬을 다시 깔기도 하였다.

****************************

결국 anaconda3 > Lib > site-packages 폴더를 찾아보았다. 



gensim 모듈이 존재하였다.



근데 비주얼 스튜디오 코드에는 실행환경을 다른 계정으로 동기화시켜두었다.



gensim 폴더를 해당 계정 폴더로 이동시켜도 문제가 해결될 것 같았지만 비주얼 코드에서 Ctrl + Shift + p를 입력하고 나오는 Python: Select Interpreter에서 계정이 아닌 anaconda 자체로 동기화하였다.


********************************

드디어 gensim이 작동하였다!



사실 주피터 노트북을 사용하면 해결되었지만 주피터 노트북을 계속 쓸 의향이 없었기 때문에 언젠가는 해결해야 할 문제라고 생각하고 매달렸다.



github push 에러 이후 가장 시간을 많이 잡아먹은 에러 같다. 거의 5시간 정도...
하지만 배운 것도 많고 (각종 에러, 아니콘다 사용법 등...) 에러도 해결해서 다행이다.

***************************

사실 gensim을 사용할 때 오류가 또 발생하긴 했는데 해결하였다. 

```
model = Word2Vec(sentences=lst_excel, vector_size=100, window=5, min_count=5, workers=4, sg=0)
```

>TypeError: __init__() got an unexpected keyword argument 'size'  



size -> vector_size
