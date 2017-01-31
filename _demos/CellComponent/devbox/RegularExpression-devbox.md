#### 정규식을 이용한 마스킹 방법

이 기능은 자바스크립트의 String.replace함수를 그대로 사용한 기능입니다.  

DataColumn의 `displayRegExp`에 찾으려는 정규식 패턴을 지정하고 `displayReplace`에 변경 패턴을 지정하면 replace된 값이 Cell에 표시됩니다.

- `displayRegExp` - 문자열 변경시(마스킹 등) 사용할 정규식 패턴을 지정합니다.
- `displayReplace` - 문자열 변경시(마스킹 등) 사용할 패턴을 지정합니다.
- [DataColumn](http://help.realgrid.com/api/types/DataColumn/)링크를 참조하세요.

<a class="btn primary small round lowercase" id="userID">사용자 Id 컬럼 마스킹 처리</a>

```js
//displayReplace에 대체문자열 사용
gridView.setColumnProperty("userid","displayRegExp", /^([a-z0-9]{3})([a-z0-9]+)$/)
gridView.setColumnProperty("userid","displayReplace", "$1***")
```

<a class="btn primary small round lowercase" id="email">E-Mail 컬럼 마스킹 처리</a>

```js
//displayReplace에 Callback 사용
gridView.setColumnProperty("email","displayRegExp", /^([a-zA-Z0-9._%+-]+)(@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4})$/)
gridView.setColumnProperty("email","displayReplace", function (match, p1, p2, offset, string) {
        return p1.substring(0, 2) + "****" + p2;
})
```

<a class="btn primary small round lowercase" id="ip_address">IP Address 컬럼 마스킹 처리</a>

```js
gridView.setColumnProperty("ip_address","displayRegExp", /^([0-9]+\.)([0-9]+\.)([0-9]+)(\.[0-9]+)$/)
gridView.setColumnProperty("ip_address","displayReplace", "$1$2***$4")
```

<a class="btn primary small round lowercase" id="card_number">신용카드 컬럼 마스킹 처리</a>

```js
gridView.setColumnProperty("card_number","displayRegExp", /^([0-9]{4})([0-9]{4})([0-9]{4})([0-9]{4})$/)
gridView.setColumnProperty("card_number","displayReplace", "$1-$2-****-$4")
```

<a class="btn primary small round lowercase" id="regularColumn">정규식을 이용한 컬럼 생성</a>

```js
var columns = [{
    "fieldName": "phone",
    "width": 120,
    "header": { "text": "전화번호" },
    "styles": {
        "textAlignment": "near",
        "font": "arial",
        "background": "#ffffff99"
    },
    "displayRegExp": /^([0-9]+)\(([0-9]+)\)([0-9]{3})([0-9]{4})$/, 
    "displayReplace": "$1-$2-$3-$4"
}];

gridView.setColumns(columns);
```

<script>
$('#userID').click(function() {
    gridView.setColumnProperty("userid","displayRegExp", /^([a-z0-9]{3})([a-z0-9]+)$/)
    gridView.setColumnProperty("userid","displayReplace", "$1***")
    gridView.setColumnProperty("userid", "styles", {background:"#ffffff99"})
});

$('#email').click(function() {
    gridView.setColumnProperty("email","displayRegExp", /^([a-zA-Z0-9._%+-]+)(@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4})$/)
    gridView.setColumnProperty("email","displayReplace", function (match, p1, p2, offset, string) {
        return p1.substring(0, 2) + "****" + p2;
    })
    gridView.setColumnProperty("email", "styles", {background:"#ffffff99"})
});

$('#ip_address').click(function() {
    gridView.setColumnProperty("ip_address","displayRegExp", /^([0-9]+\.)([0-9]+\.)([0-9]+)(\.[0-9]+)$/)
    gridView.setColumnProperty("ip_address","displayReplace", "$1$2***$4")
    gridView.setColumnProperty("ip_address", "styles", {background:"#ffffff99"})
});

$('#card_number').click(function() {
    gridView.setColumnProperty("card_number","displayRegExp", /^([0-9]{4})([0-9]{4})([0-9]{4})([0-9]{4})$/)
    gridView.setColumnProperty("card_number","displayReplace", "$1-$2-****-$4")
    gridView.setColumnProperty("card_number", "styles", {background:"#ffffff99"})
});

$('#regularColumn').click(function() {
    var columns = [{
	    "fieldName": "phone",
	    "width": 120,
	    "header": { "text": "전화번호" },
	    "styles": {
	        "textAlignment": "near",
	        "font": "arial",
	        "background": "#ffffff99"
	    },
	    "displayRegExp": /^([0-9]+)\(([0-9]+)\)([0-9]{3})([0-9]{4})$/, 
	    "displayReplace": "$1-$2-$3-$4"
	}];

	gridView.setColumns(columns);
});
</script>