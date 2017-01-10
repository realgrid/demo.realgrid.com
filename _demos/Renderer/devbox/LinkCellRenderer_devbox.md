#### 링크 렌더러

Link Renderer에서 Url을 지정하는 방법은 `Url형태의 값을 가진 필드를 지정`하거나 `수식으로 Url Format를 지정`하는 방법 두 가지가 있습니다.  

* UrlField로 지정하는 경우로 지정된 필드의 값을 모두 Url로 인지합니다. 
* 경우 Url 속성으로 Format을 지정할 수 있습니다.  

예를들어 `url: "http://demo.realgrid.net${Page}"` 로 하면 Page라는 필드명에 앞에 초기 경로를 지정할 수 있습니다.  (JSP의 경우 ${...}는 EL로 인식됩니다. 따라서 문자열을 나누어 Url의 필드를 지정해야 합니다. `"$"+"{field}"`) 

Link 셀 렌더러에서 Hovering중일 때 문자열의 아래에 `Underline`으로 표시됩니다.  
이 때 클릭하면 [onLinkableCellClicked](http://help.realgrid.com/api/GridBase/onLinkableCellClicked/)이벤트가 발생하며 url parameter에 지정된 `url`값이 전달됩니다.  
(`Link Renderer에 기존 Icon Renderer의 속성을 모두 사용할 수 있습니다.`)

#### 링크 설정

[LinkCellRenderer](http://help.realgrid.com/api/types/LinkCellRenderer/)에서 사용할 수 있는 속성들 입니다.

* `url` - 필드값을 url Format값으로 사용할 url을 지정합니다.
* `urlField` - url 형태의 값을 가진 필드를 지정합니다.
* `showUrl` - url을 ToolTip창으로 표시할것인지를 지정합니다.
* `requiredFields` - url 표현식으로 지정할때 표현식에 포함된 필드값중에 빈값이면 안되는 field명을 콤마(,)로 구분하여 입력합니다.  
(`requiredFields`에 명시된 필드중 하나이상이 빈값인 경우 해당 셀은 `Hyperlink`가 생기지 않습니다.)

#### 링크 적용하기

버튼을 클릭해서 `Country` 컬럼에 링크를 적용해 보세요.  
Country 컬럼에 링크가 설정되며 url주소를 tooltip으로 표시해 줍니다.

<a class="btn primary small round lowercase" id="btnLinkCountry">링크 적용</a>

```js
gridView.setColumnProperty("Country", "renderer", {
    type: "link",
    url: "http://www.countryreports.org/country/${Country}.htm",
    requiredFields: "Country",
    showUrl: true
});
```

버튼을 클릭해서 `CompanyName` 컬럼에 링크를 적용해 보세요.  
CompanyName 컬럼에 링크가 설정되며 url주소를 tooltip으로 표시하지 않습니다.

<a class="btn primary small round lowercase" id="btnLinkCompanyName">링크 적용</a>

```js
gridView.setColumnProperty("CompanyName", "renderer", {
    type: "link",
    url: "https://www.google.co.kr/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#newwindow=1&q=${CompanyName}",
    requiredFields: "CompanyName",
    showUrl: false
});
```

버튼을 클릭해서 페이지를 띄우기 위한 이벤트를 적용해 보세요.

<a class="btn primary small round lowercase" id="btnLinkEvent">이벤트 적용</a>

```js
gridView.onLinkableCellClicked = function (grid, index, url) {
    alert(url + "  페이지를 띄웁니다.");
    window.open(url, '_newtab');
};
```

<script>
$('#btnLinkCountry').click(function() {
	gridView.setColumnProperty("Country", "renderer", {
	    type: "link",
	    url: "http://www.countryreports.org/country/${Country}.htm",
	    requiredFields: "Country",
	    showUrl: true
	});
});

$('#btnLinkCompanyName').click(function() {
	gridView.setColumnProperty("CompanyName", "renderer", {
	    type: "link",
	    url: "https://www.google.co.kr/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#newwindow=1&q=${CompanyName}",
	    requiredFields: "CompanyName",
	    showUrl: false
	});
});

$('#btnLinkEvent').click(function() {
	gridView.onLinkableCellClicked = function (grid, index, url) {
	    alert(url + "  페이지를 띄웁니다.");
	    window.open(url, '_newtab');
	};
});

</script>