#### pivot 정렬
피벗 그리드를 label이나 value 기준으로 정렬하려 할 때 사용합니다.  
[http://help.realgrid.com/pivotApi/RealPivot/sort/](http://help.realgrid.com/pivotApi/RealPivot/sort/)
[http://help.realgrid.com/pivotApi/types/SortMethod/](http://help.realgrid.com/pivotApi/types/SortMethod/)
[http://help.realgrid.com/pivotApi/types/SortDirection/](http://help.realgrid.com/pivotApi/types/SortDirection/)

#### label 기준 정렬

<a class="btn primary small round lowercase" id="btnSetLabelSort">label 기준 정렬</a>

```js
pivot.sort({
  column: {
      method: "label",
      labels: [  
        { name: "판매분기", direction: "descending"}
     ]
  },
  row: {
    method:"label",
    labels: [  
        { name: "브랜드명", direction: "descending"}
     ]
  }
});
```

<!--
#### value 기준 정렬

<a class="btn primary small round lowercase" id="btnSetValueSort">value 기준 정렬</a>

```js
pivot.sort({
  row: {
      method: "value",
      fieldName: "차량가격", 
      direction: "descending"
  }
});
```
-->
<script>
$('#btnSetLabelSort').click(function() {
	pivot.sort({
	  column: {
	      method: "label",
	      labels: [  
	        { name: "판매분기", direction: "descending"}
	     ]
	  },
	  row: {
	    method:"label",
	    labels: [  
	        { name: "브랜드명", direction: "descending"}
	     ]
	  }
	});
});
/*
$('#btnSetValueSort').click(function() {
	pivot.sort({
	  row: {
	      method: "value",
	      fieldName: "차량가격", 
	      direction: "descending"
	  }
	});
});
*/
</script>