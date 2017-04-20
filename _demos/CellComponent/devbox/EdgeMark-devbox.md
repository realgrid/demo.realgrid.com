#### 엣지마크 표시하기
Column.Styles에 figureName 에 [EdgeMark](http://help.realgrid.com/api/types/EdgeMark/)를 지정하면 해당 위치에 삼각형 표식이 나타난다.  
색상은 figureBackground로 지정하며 figureSize로 크기를 지정한다. 
figureSize는 %, 정수 형태로 값을 지정할 수 있으며, % 형태로 값을 지정하면 행의 높이 비율만큼의 크기로 표시되며 정수 형태인 경우는 그 수만큼의 픽셀 크기로 표시된다.  

```js
var columns = [{
  "name": "OrderID",
  "fieldName": "OrderID",
  "type": "data",
  "width": "90",
  "styles": {
      "textAlignment": "center",
      "figureName": "leftTop", 
      "figureBackground": "#FFFF0000", 
      "figureSize": "50%"
  },
  "header": {
      "text": "Order ID"
  }
}, {
  "name": "CustomerID",
  "fieldName": "CustomerID",
  "type": "data",
  "width": "130",
  "styles": {
      "textAlignment": "center",
      "figureName": "rightTop", 
      "figureBackground": "#FF0000FF", 
      "figureSize": "7"
  },
  "header": {
      "text": "Customer ID"
  }
},
...
];
gridView.setColumns(columns);
```

#### 동적으로 엣지마크 적용하기

Employee ID가 5 인것만 엣지마크 적용하기

<a class="btn primary small round lowercase" id="setEmployeeID">적용하기</a>

```js
var dStyles = [{
  criteria: "value = '5'",
  styles: {
    "textAlignment": "center",
    "figureName": "rightBottom", 
    "figureBackground": "#FF0000FF", 
    "figureSize": "7"
  }
}];

gridView.setColumnProperty("EmployeeID", "dynamicStyles", dStyles);

```


<script>
$('#setEmployeeID').click(function() {
	var dStyles = [{
		criteria: "value = '5'",
		styles: {
		  "textAlignment": "center",
	      "figureName": "rightBottom", 
	      "figureBackground": "#FFFF0FF0", 
	      "figureSize": "7"
	    }
	}];

	gridView.setColumnProperty("EmployeeID", "dynamicStyles", dStyles);
});

</script>