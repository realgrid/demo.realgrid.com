#### 셀값 가져오기

현재 포커스가 있는셀의 데이터가 어떤 행으로 이루어진 데이터인지 확인한다.
<a class="btn primary small round lowercase" id="btnGetCellValuesAt">셀값 가져오기</a>

생략하면 현재 focus 기준으로 값을 가져온다.

```js
alert(JSON.stringify(pivot.getCellValuesAt()));
//또는
//pivot.getCellValuesAt(pivot.getCurrent());
```


<script>
	$('#btnGetCellValuesAt').click(function() {	
	    alert(JSON.stringify(pivot.getCellValuesAt()));
    });
</script>