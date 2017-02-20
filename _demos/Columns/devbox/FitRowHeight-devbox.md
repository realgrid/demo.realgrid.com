#### 행 높이 개별 설정하기

개별행 높이를 설정하기 위해서 
[DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)에 `eachRowResizable`속성을 true로 설정합니다.

<a class="btn primary small round lowercase" id="eachRowResizable">행 높이 개별 조절 가능</a>

```js
gridView.setDisplayOptions({eachRowResizable:true});
```

아래는 개별 행 높이 관련 API입니다.

* [fitRowHeight(itemIndex, maxHeight, textOnly, refresh)](http://help.realgrid.com/api/GridBase/fitRowHeight/)
* [fitRowHeightAll(maxHeight, textOnly)](http://help.realgrid.com/api/GridBase/fitRowHeightAll/)
* [setRowHeight(itemIndex, height, refresh)](http://help.realgrid.com/api/GridBase/setRowHeight/)
* [clearRowHeights(refresh)](http://help.realgrid.com/api/GridBase/clearRowHeights/)

`fitRowHeight` 함수는 특정 행의 행 높이를 데이터 높이에 맞게 설정합니다.

<a class="btn primary small round lowercase" id="fitRowHeight">데이터 높이에 맞게 설정</a>

```js
var itemIndex = gridView.getCurrent().itemIndex;
gridView.fitRowHeight(itemIndex, 0, true, true);
```

`fitRowHeightAll` 함수는 전체 행 높이를 데이터 높이에 맞게 설정합니다.

<a class="btn primary small round lowercase" id="fitRowHeightAll">전체 행 높이 설정</a>

```js
gridView.fitRowHeightAll(0, true);
```

`setRowHeight` 함수는 특정 행의 행 높이를 지정한 높이로 변경합니다. 

<a class="btn primary small round lowercase" id="setRowHeight">개별 행 높이 설정</a>

```js
var itemIndex = gridView.getCurrent().itemIndex;
gridView.setRowHeight(itemIndex, 100, true);
```

`clearRowHeights` 함수는 특정 행의 행 높이를 지정한 높이로 변경합니다. 

<a class="btn primary small round lowercase" id="clearRowHeights">설정 되돌리기</a>

```js
gridView.clearRowHeights(true);
```

#### 개별 행 높이 설정이 불가능한 경우

1. columnGroup.`vertical`이 있는 경우에는 적용되지 않습니다.  
2. rowGroup상태일때는 `groupHeader`, `groupFooter`의 경우 조절 불가능 합니다.

<script>
	$('#eachRowResizable').click(function() {
		gridView.setDisplayOptions({eachRowResizable:true});
	});

	$('#fitRowHeight').click(function() {
		var itemIndex = gridView.getCurrent().itemIndex;
		gridView.fitRowHeight(itemIndex, 0, true, true);
	});

	$('#fitRowHeightAll').click(function() {
		gridView.fitRowHeightAll(0, true);
	});

	$('#setRowHeight').click(function() {
		var itemIndex = gridView.getCurrent().itemIndex;
		gridView.setRowHeight(itemIndex, 100, true);
	});

	$('#clearRowHeights').click(function() {
		gridView.clearRowHeights(true);
	});
</script>