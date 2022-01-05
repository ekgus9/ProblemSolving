# Github Push Error Solution



github 관련 에러는 깃허브를 시작하고 엄청 초기에 겪은 문제라 자세히 기억나지는 않는다.



그러나 이제는 push에서 만큼은 해결책을 찾았다고 생각한다.



> ! [rejected]        master -> master (non-fast-forward)



특히 push할 때 위 에러가 정말 고통스러웠다. 

```
git push -f origin main
```

위 코드를 사용해서 강제로 push하는 방법도 있었지만, 



이를 사용하면 올리고 싶지 않은 파일까지 push 되거나 해당 폴더에 없는 파일은 깃허브에서도 사라지는 문제가 발생하였다.

*********

깃허브에 push할 때는 다음 순서대로만 하면 아무 이상이 없었다.

```
git init
git add *
git pull origin main
git commit -m ""
git push -u origin main
```

\*부분에는 push하고 싶은 파일을 입력하고, commit message 입력도 필수이다.

**********

만약 message를 잘못 입력하였다면 다음과 같은 코드를 사용하여 수정할 수 있다.
```
git commit --amend -m "input and output"
```

*******
>fatal: 'origin' does not appear to be a git repository



>fatal: Could not read from remote repository.



이러한 오류가 뜬다면 다음 코드를 입력해준다. (주소는 push하고 싶은 repository 주소로 입력)

```
git remote add origin https://github.com/ekgus9/ProblemSolving.git
```

************

>Author identity unknown



>\*\*\* Please tell me who you are.



위 오류는 가끔 뜨는데, 자신의 이메일과 이름을 입력하면 해결된다.

```
git config --global user.email "dhaabb55@naver.com"
git config --global user.name "ekgus9"
```

*************

> fatal: remote origin already exists.



해당 에러는 기존 레파지토리와의 연결을 끊고 새 주소를 입력해주어야 한다.

```
git remote remove origin
git remote add origin https://github.com/ekgus9/ProblemSolving.git
```

********

\+



요즘은 아래 코드를 그대로 입력해도 잘 push 된다.

```
git init
git add *
git commit -m ""
git branch -M main
git remote add origin https://github.com/ekgus9/ProblemSolving.git
git push -u origin main
```

*********
\+\+


```
git status
```

위 명령어를 통해 git branch나 add, commit 상태를 알아볼 수 있다.


