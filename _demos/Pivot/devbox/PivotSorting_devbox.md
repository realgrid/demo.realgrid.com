#### 피벗 정렬

피벗에서 정렬하는 방식은 라벨 기준 정렬 방식과 특정 조건의 값 기준 정렬방식이 있습니다.  
라벨 정렬은 컬럼/행에 존재하는 라벨기준 정렬이고, 값 정렬은 `일사분기 판매수량 합계가 큰 순서대로 정렬한다`와 같은 조건을 부여할 수 있습니다.  

피벗에서 데이터를 정렬하는 방법은 다음과 같습니다.

1. [setFieldMapping()](http://help.realgrid.com/pivotApi/RealPivot/setFieldMapping/){:target="_blank"}호출 시 [PivotField](http://help.realgrid.com/pivotApi/types/PivotField/){:target="_blank"}의 [sortDir속성](http://help.realgrid.com/pivotApi/types/SortDirection/){:target="_blank"}을 기본 정렬을 지정하는 방법 (라벨 정렬만 해당)

2. [sort()](http://help.realgrid.com/pivotApi/RealPivot/sort/){:target="_blank"} 함수로 정렬하는 방법 (라벨정렬과 값정렬 모두 해당)
3. 피벗내 Setup UI를 이용한 방법

#### 라벨값 기준 정렬
라벨 기준 정렬시 labels 속성이 필요합니다. 
labels 속성에는 각 필드들의 이름과 [정렬 순서](http://help.realgrid.com/pivotApi/types/SortDirection/){:target="_blank"}을 지정합니다.  
<a class="btn primary small round lowercase" id="btnLabelSort">라벨 기준 정렬</a>


```js
pivot.sort({
  column: {
      method: "label",
      labels: [  
        { name: "판매분기", direction: "descending"},
        { name: "판매월", direction: "descending"}
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
      direction: "descending",
      conditions: [{
      	name: "판매년도", value: 2016
      }]
  }
});
```

#### 복합 정렬
피벗에서 컬럼과 행의 정렬 기준을 각각 따로 지정할 수 있습니다.

<a class="btn primary small round lowercase" id="btnComplexSort">복합 정렬</a>

```js
pivot.sort({
  column: {
      method: "label",
      labels: [  
        { name: "판매분기", direction: "descending"},
        { name: "판매월", direction: "descending"}
     ]
  },
  row: {
      method: "value",
      fieldName: "판매수량", 
      direction: "descending",
      conditions: [{
      	name: "판매년도", value: 2016
      }]
  }
});
```

<script>
$('#btnLabelSort').click(function() {
	pivot.sort({
	  column: {
	      method: "label",
	      labels: [  
	        { name: "판매분기", direction: "descending"},
	        { name: "판매월", direction: "descending"}
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
	      	name: "판매년도", value: 2016
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
	        { name: "판매월", direction: "descending"}
	     ]
	  },
	  row: {
	      method: "value",
	      fieldName: "판매수량", 
	      direction: "descending",
	      conditions: [{
	      	name: "판매년도", value: 2016
	      }]
	  }
	});
});

</script>