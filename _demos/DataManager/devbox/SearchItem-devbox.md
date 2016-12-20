#### 검색 조건 설정하기

[SearchOptions](http://help.realgrid.com/api/types/SearchOptions/)는 그리드에 현재 표시된 행들 중에서 특정한 행을 찾는 조건을 지정합니다.

```js
var values = [$("#txtSearch").val()];
var caseSensitive = $(':radio[name="case"]:checked').val() == "case";
var partialMatch = $(':radio[name="partial"]:checked').val() == "partial";
var wrap = $(':radio[name="wrap"]:checked').val() == "wrap";
var startIndex = (gridView.getCurrent().itemIndex + 1) % gridView.getItemCount();
if (gridView.getCurrent().itemIndex == gridView.getItemCount() - 1)
    startIndex = 0;

var options = {
    fields: ["브랜드명"],
    values: values,
    startIndex: startIndex,
    caseSensitive: caseSensitive,
    partialMatch: partialMatch,
    wrap: wrap,
    select: false
}
```

#### 검색하기

[searchItem()](http://help.realgrid.com/api/GridBase/searchItem/)함수를 사용해서 지정한 필드들의 값에 해당하는 첫번째 행을 찾아 행의 번호를 반환합니다.

```js
var index = gridView.searchItem(options);
```


#### 포커스 이동하기

[searchItem()](http://help.realgrid.com/api/GridBase/searchItem/)에서 반환한 첫번째 행으로 포커스를 이동합니다.

```js
gridView.setCurrent({
    itemIndex: index,
    column: "브랜드명"
});

gridView.setFocus();
```

#### 브랜드명 검색해보기

<input type="text" id="txtSearch" placeholder="검색할 브랜드명 입력" style="width:200px; height:30px">

---

**대소문자 구분 설정**  
<input type="radio" name="case" value="case"><label style="vertical-align:middle">대소문자 구분</label>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="case" value="" checked="checked"><label style="vertical-align:middle">구분하지 않음</label>

---

**부분 일치 설정**  
<input type="radio" name="partial" value="partial"><label style="vertical-align:middle">부분 일치</label>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="partial" value="" checked="checked"><label style="vertical-align:middle">모두 일치</label>

---

**처음부터 다시 검색**  
<input type="radio" name="wrap" value="wrap" checked="checked"><label style="vertical-align:middle">처음부터 다시 검색</label>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="wrap" value="always"><label style="vertical-align:middle">검색을 종료</label>

---

<a class="btn primary small round lowercase" id="btnSearch">검색하기</a>



<script>
$('#btnSearch').click(function() {
	var values = [$("#txtSearch").val()];
	var caseSensitive = $(':radio[name="case"]:checked').val() == "case";
	var partialMatch = $(':radio[name="partial"]:checked').val() == "partial";
	var wrap = $(':radio[name="wrap"]:checked').val() == "wrap";
	var startIndex = (gridView.getCurrent().itemIndex + 1) % gridView.getItemCount();
	if (gridView.getCurrent().itemIndex == gridView.getItemCount() - 1)
	    startIndex = 0;

	var options = {
	    fields: ["브랜드명"],
	    values: values,
	    startIndex: startIndex,
	    caseSensitive: caseSensitive,
	    partialMatch: partialMatch,
	    wrap: wrap,
	    select: false
	}

	var index = gridView.searchItem(options);
	var index = gridView.searchItem(options);
    if (index < 0) {
        alert("검색 결과가 없습니다!");
        return;
    }

	gridView.setCurrent({
	    itemIndex: index,
	    column: "브랜드명"
	});
});
</script>