#### 피벗 정렬
피벗에서 [method 속성](http://help.realgrid.com/pivotApi/types/SortMethod/){:target="_blank"}을 지정하여 라벨값 또는 값을 기준으로 정렬할 수 있습니다.  
라벨값 정렬은 컬럼/행에 표시되는 라벨의 알파벳 정렬이고,
값 정렬은 특정 조건의 값을 기준으로 하는 정렬입니다. (예, 일사분기 판매수량 합계 역순으로 행을 정렬)  


#### 라벨값 기준 정렬
라벨값 기준 정렬시 labels 속성이 필요합니다. 
labels 속성에는 각 필드들의 이름과 [정렬 순서](http://help.realgrid.com/pivotApi/types/SortDirection/){:target="_blank"}을 지정합니다.  
<a class="btn primary small round lowercase" id="btnLabelSort">라벨값 기준 정렬</a>


```js
pivot.sort({
  column: {
      method: "label",
      labels: [  
        { name: "판매분기", direction: "descending"},
        { name: "월", direction: "descending"}
     ]
  },
  row: {
    method:"label",
    labels: [  
        { name: "브랜드명", direction: "ascending"},
        { name: "차종", direction: "ascending"}
     ]
  }
});
```

#### 값 기준 정렬
값 기준 정렬시 값필드 명(fieldName)과 [정렬 순서](http://help.realgrid.com/pivotApi/types/SortDirection/){:target="_blank"} 그리고 정렬조건을 지정합니다.  
conditions 속성은 정렬할 조건으로 column의 경우 행 필드가, row의 경우 컬럼 필드가 조건으로 명시되어야 합니다.  
conditions가 생략되면 전체 요약 기준으로 정렬합니다.  

<a class="btn primary small round lowercase" id="btnValueSort">판매수량 값 기준 정렬</a>

```js
pivot.sort({
  column: {
      method: "value",
      fieldName: "판매수량",
      direction: "descending",
  },
  row: {
      method: "value",
      fieldName: "판매수량", 
      direction: "descending"
      conditions: [{
      	name: "판매분기", value: 0
      }]
  }
});
```

#### 복합 정렬
피벗에서 컬럼과 행의 정렬 기준을 따로 지정할 수 있습니다.

<a class="btn primary small round lowercase" id="btnComplexSort">복합 기준 정렬</a>

```js
pivot.sort({
  column: {
      method: "label",
      labels: [  
        { name: "판매분기", direction: "descending"},
        { name: "월", direction: "descending"}
     ]
  },
  row: {
      method: "value",
      fieldName: "판매수량", 
      direction: "descending"
      conditions: [{
      	name: "판매분기", value: 0
      }]
  }
});
```

#### API LINK
[sort()](http://help.realgrid.com/pivotApi/RealPivot/sort/){:target="_blank"}  


<script>
$('#btnLabelSort').click(function() {
	pivot.sort({
	  column: {
	      method: "label",
	      labels: [  
	        { name: "판매분기", direction: "descending"},
	        { name: "월", direction: "descending"}
	     ]
	  },
	  row: {
	    method:"label",
	    labels: [  
	        { name: "브랜드명", direction: "ascending"},
	        { name: "차종", direction: "ascending"}
	     ]
	  }
	});
});

$('#btnValueSort').click(function() {
	pivot.sort({
	  column: {
	      method: "value",
	      fieldName: "판매수량",
	      direction: "descending",
	  },
	  row: {
	      method: "value",
	      fieldName: "판매수량", 
	      direction: "descending",
	      conditions: [{
	      	name: "판매분기", value: 0
	      }]
	  }
	});
});

$('#btnComplexSort').click(function() {
	pivot.sort({
	  column: {
	      method: "label",
	      labels: [  
	        { name: "판매분기", direction: "descending"},
	        { name: "월", direction: "descending"}
	     ]
	  },
	  row: {
	      method: "value",
	      fieldName: "판매수량", 
	      direction: "descending",
	      conditions: [{
	      	name: "판매분기", value: 0
	      }]
	  }
	});
});

</script>