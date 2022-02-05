# Selenium Error



> usb_device_handle_win.cc:1020 Failed to read descriptor from node connection:  시스템에 부착된 장치가 작동하지 않습니다. (0x1F)



이 에러는 아래 코드와 같이 옵션을 추가하면 등장하지 않는다.

```
options = webdriver.ChromeOptions()
options.add_experimental_option("excludeSwitches", ["enable-logging"])
driver = webdriver.Chrome("<chrome driver 경로>",options=options)
```

참고 : <https://althoughh.tistory.com/82>
