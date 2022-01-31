# tsv 파일 열기



tsv 파일은 탭 tab 으로 구분된 파일이다. 이 또한 csv 파일과 같이 pandas의 read_csv를 사용하여 열 수 있다. 
아래 코드와 같이 함수 안에 sep = '\t'를 지정해주거나 delimiter = '\t'를 지정해주면 열린다.

```
df = pd.read_csv('df.tsv', sep = '\t')
```

-------------



> parsererror: error tokenizing data. c error: expected 2 fields in line 43043, saw 3



위와 같은 에러는 내 경우에는 에러 코드에 적힌 부분에 컴퓨터가 구분자로 인식할 법한 쉼표(,)가 있있기 때문에 발생하였다. 
따라서 다음 코드를 사용하여 해당 행을 무시하였다.

```
df = pd.read_csv('df.csv', error_bad_lines=False)
```

이 에러에 대한 더 많은 정보는 아래 사이트에 있다.



<https://stackoverflow.com/questions/18039057/python-pandas-error-tokenizing-data>
