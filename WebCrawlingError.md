# web crawling error



웹 페이지를 크롤링하기 위해 beautifulsoup을 사용하고 있었다. 하지만 특정 웹페이지에서 특정 부분이 계속 크롤링 되지 않아 결과가 None으로 나오는 문제가 발생하였다.
이를 해결하기 위해 서치를 하던 도중 첫번째 문제를 해결할 수 있었다. 



- 문제 1 : 동적 페이지



url에 따라서 정해진 페이지를 불러오는 것을 정적 Static 페이지라고 하며, url에 상관없이 웹페이지 위에서 데이터를 불러오는 방법을 동적 Dynamic 페이지라고 한다. 동적 페이지는 페이지에 접속하면 유저의 행동 결과에 따라 소스 코드가 변하므로 beautifulsoup보다는 selenium을 사용하여 크롤링을 진행하여야 한다. 물론 beautifulsoup의 속도가 더 빨라 가능하다면 beautifulsoup를 사용하는 게 효율적이지만, 동적 페이지에는 한계가 있다. 



나의 경우에도 url은 동일하지만 페이지에서 어떤 것을 선택하느냐에 따라 다른 정보를 제공하는 페이지를 크롤링하고자 하였다. 따라서 selenium을 이용하여 크롤링을 진행하였다. 그러나 이 문제만이 크롤링 되지 않는 원인이 아니었다. 대체 왜 페이지에 정보도 보이고, 개발자 도구를 통해 보이는 path도 존재하는데 크롤링이 안되는 건지 너무 답답했다. 



- 문제 2 : iframe



> selenium.common.exceptions.NoSuchElementException: Message: no such element: Unable to locate element: {"method":"xpath","selector":"//*[@id="form1"]/table/tbody/tr[4]"}



요소를 찾을 수 없는 위 에러의 원인은 iframe이었다. ifram을 한마디로 말하자면 창 속의 창이다. 그냥 보기에는 하나의 창으로 보이지만 사실은 여러 개의 창이 겹쳐있는 것이다. 따라서 실제로 크롤링하고자 하는 데이터는 다른 창에 있는데, 엉뚱한 창을 계속 크롤링하고 있던 것이다. 개발자 도구에서도 iframe의 존재를 다음과 같이 확인할 수 있다.



![image](https://user-images.githubusercontent.com/89879599/152642926-200a8d23-15d3-4605-9ee0-af1aa3d2468f.png)



아래 코드를 이용하여 ifame의 여부와 이름을 확인할 수 있다.

```
iframes = driver.find_elements_by_css_selector('iframe') 
for iframe in iframes:
    print(iframe.get_attribute('name'))
```

아래 코드는 iframe의 이름을 넣어 해당 iframe으로 이동할 수 있는 코드이다.

```
driver.switch_to.frame('menuiframe')
```

다시 메인 프레임으로 나오기 위해서는 아래 코드가 필요하다.

```
driver.switch_to.parent_frame()
```

참고 : <https://nanchachaa.tistory.com/38>
