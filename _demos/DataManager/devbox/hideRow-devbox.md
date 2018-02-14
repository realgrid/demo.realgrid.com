#### 그리드 행 숨기기

아래는 그리드 행을 숨기기 위한 함수들 입니다.

* [hideRows()](http://help.realgrid.com/api/DataProvider/hideRows/)
* [showHiddenRows()](http://help.realgrid.com/api/DataProvider/showHiddenRows/)
* [getHiddenRows()](http://help.realgrid.com/api/DataProvider/getHiddenRows/)
* [isHiddenRow()](http://help.realgrid.com/api/DataProvider/isHiddenRow/)


<a class="btn primary small round lowercase" id="btnHideRows">hideRows 실행</a>

[0,3,5] 행들을 화면에서 표시하지 않는다

```js
dataProvider.hideRows([0,3,5]);
```


<a class="btn primary small round lowercase" id="btnShowHiddenRows">showHiddenRows 실행</a>

hideRows()로 숨긴 행들 중  3 행을 화면에 다시 표시한다.

```js
dataProvider.showHiddenRows([3]);
```

<a class="btn primary small round lowercase" id="btnGetHiddenRows">getHiddenRows 실행</a>

숨긴 행의 정보를 가져옵니다.

```js
alert(dataProvider.getHiddenRows());
```

<a class="btn primary small round lowercase" id="btnIsHiddenRow">isHiddenRow 실행</a>

3 행이 숨긴 행인지 확인한다.

```js
alert(dataProvider.isHiddenRow(5));
```

#### 숨긴 모든 행 다시 표시

* [resetHiddenRows()](http://help.realgrid.com/api/DataProvider/resetHiddenRows/)

<a class="btn primary small round lowercase" id="btnResetHiddenRows">숨겨진 행 초기화</a>

숨긴 모든 행을 다시 표시합니다.

```js
dataProvider.resetHiddenRows();
```

<script>
    $('#btnHideRows').click(function() {
    	dataProvider.hideRows([0,3,5]);
    });

    $('#btnShowHiddenRows').click(function() {
    	dataProvider.showHiddenRows([3]);
    });

    $('#btnGetHiddenRows').click(function() {
    	alert(dataProvider.getHiddenRows());
    });

    $('#btnIsHiddenRow').click(function() {
    	alert(dataProvider.isHiddenRow(5));
    });

    $('#btnResetHiddenRows').click(function() {
    	dataProvider.resetHiddenRows();
    });
</script>