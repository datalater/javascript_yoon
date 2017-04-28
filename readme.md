ⓒ JMC 2017

주요 소스: 모던 웹을 위한 JavaScript 및 jQuery 입문, 윤인성

---

# Untitled

## 현재 시간 표시 (코드 10-27)

### 코드

```
> document.body.innerHTML = "<h1 id='clock'></h1>"
> var clock = document.getElementById('clock');
> setInterval(function () {
    clock.innerHTML = new Date().toString();
}, 1000);
```

+ 1초마다 시간이 바뀐다.

### 설명

+ `document.body.innerHTML` : HTML 내용을 문서의 body 태그 안에 넣는다.

---
