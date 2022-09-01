#### 셀 값 가져오기

현재 포커스가 있는셀의 데이터가 어떤 행으로 이루어진 데이터인지 확인한다.
<a class="btn primary small round lowercase" id="btnGetCellValuesAt">셀 값 가져오기</a>

```js
alert(JSON.stringify(pivot.getCellValuesAt()));
```


<script>
	$('#btnGetCellValuesAt').click(function() {	
	    alert(JSON.stringify(pivot.getCellValuesAt()));
    });
</script>