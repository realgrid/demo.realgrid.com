#### 정규식 패턴 지정

이 기능은 자바스크립트의 String.replace함수를 그대로 사용한 기능입니다.  

DataColumn의 `displayRegExp`에 찾으려는 정규식 패턴을 지정하고 `displayReplace`에 변경 패턴을 지정하면 replace된 값이 Cell에 표시됩니다.

사용자 Id 컬럼

```js
//displayReplace에 대체문자열 사용
displayRegExp: /^([a-z0-9]{3})([a-z0-9]+)$/, 
displayReplace: "$1***"
```

E-Mail 컬럼

```js
//displayReplace에 Callback 사용
displayRegExp: /^([a-zA-Z0-9._%+-]+)(@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4})$/,
displayReplace:
    function (match, p1, p2, offset, string) {
        return p1.substring(0, 2) + "****" + p2;
    }
```