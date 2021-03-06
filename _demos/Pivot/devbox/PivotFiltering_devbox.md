#### 필터링 설정
conditions속성으로 필터 조건을 지정하고 [operation](http://help.realgrid.com/api/types/FilteringOptions/){:target="_blank"}속성에 조건간의 연산방식을 지정합니다.
conditions에는 criteria로 식을 지정하거나, values에 특정 값을 지정할 수 있습니다.  


 <a class="btn primary small round lowercase" id="btnSetFilter1">이사분기 이상이고 차종이 기아,현대로 필터링</a>

```js
pivot.filter({
    operation: "and",  // and | or
    conditions: [
        { name: "판매분기", criteria: "value >= 2" },
        { name: "브랜드명", values: ["기아", "현대"] }
    ]
});
```

<a class="btn primary small round lowercase" id="btnSetFilter2">판매월이 9월이후이고 중형으로 필터링</a>

```js
pivot.filter({
    operation: "and",  // and | or
    conditions: [
        { name: "판매월", criteria: "value >= 9" },
        { name: "차종", values: ["중형"] }
    ]
});
```

<a class="btn primary small round lowercase" id="btnResetFilter">필터 초기화</a>

```js
pivot.resetFilter();
```

#### API LINK

[filter()](http://help.realgrid.com/pivotApi/RealPivot/filter/)

<script>
$('#btnSetFilter1').click(function() {
	pivot.filter({
	    operation: "and",  // and | or
	    conditions: [
	        { name: "판매분기", criteria: "value >= 2" },
	        { name: "브랜드명", values: ["기아", "현대"] }
	    ]
	});
});

$('#btnSetFilter2').click(function() {
	pivot.filter({
	    operation: "and",  // and | or
	    conditions: [
	        { name: "판매월", criteria: "value >= 9" },
	        { name: "차종", values: ["중형"] }
	    ]
	});
});

$('#btnResetFilter').click(function () {
	pivot.resetFilter();
})
</script>