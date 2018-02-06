#### 필터링 설정

판매분기, 브랜드명의 조건으로 필터링합니다. 

<a class="btn primary small round lowercase" id="btnSetFilter1">필터링 옵션 적용</a>

```js
pivot.filter({
    operation: "and",  // and | or
    conditions: [
        { name: "판매분기", criteria: "value >= 2" },
        { name: "브랜드명", criteria: "value = '기아'" }
    ]
});
```
판매월, 차종의 조건으로 필터링합니다.

<a class="btn primary small round lowercase" id="btnSetFilter2">필터링 옵션 적용</a>

```js
pivot.filter({
    operation: "and",  // and | or
    conditions: [
        { name: "판매월", criteria: "value >= 10" },
        { name: "차종", criteria: "value = '중형'" }
    ]
});
```

<script>
$('#btnSetFilter1').click(function() {
	pivot.filter({
	    operation: "and",  // and | or
	    conditions: [
	        { name: "판매분기", criteria: "value >= 2" },
	        { name: "브랜드명", criteria: "value = '기아'" }
	    ]
	});
});

$('#btnSetFilter2').click(function() {
	pivot.filter({
	    operation: "and",  // and | or
	    conditions: [
	        { name: "판매월", criteria: "value >= 10" },
	        { name: "차종", criteria: "value = '중형'" }
	    ]
	});
});
</script>