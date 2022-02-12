# Python Syntax Error



> SyntaxError: Non-UTF-8 code starting with '\xeb' in file c:\Users\user\OneDrive\문서\파이썬\netflix\separate.py on line 8, but no encoding declared; see https://python.org/dev/peps/pep-0263/ for details



한글 인코딩 문제로, 파이썬 코드 맨 위에 아래 코드를 입력해주면 해결된다. 

```
# -*- coding: utf-8 -*-
```

참고: <https://tom7930.tistory.com/57>
