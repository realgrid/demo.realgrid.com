#### 도형 표시 방법

`shapeCellRenderer`에 도형을 설정 해보겠습니다.

도형을 표시하기 위해서는 renderer의 type은 `shape`로 설정합니다.

```js
renderer: {
    type: "shape"
}
```

다음으로 도형컬럼에 도형과 style을 설정합니다.

* Shape 타입은 `figureName` 속성으로 지정합니다.  
* Shape는 컬럼 스타일의 `figureSize` 설정으로 크기를 자유롭게 지정할 수 있습니다.  
* `figureBackground`로 색상 또한 다양하게 설정할 수 있습니다.  
* [PolygonShape](http://help.realgrid.com/api/types/PolygonShape/)
* [ShapeCellRenderer](http://help.realgrid.com/api/types/ShapeCellRenderer/)

```js
styles: {
    figureBackground: "#ff008800",
    figureName: "minus",
    iconLocation: "right",
    figureSize: "50%",
    paddingRight: 6
}
```

#### 도형 표시하기

버튼 클릭시 `OrderID` 컬럼에 원 도형을 표시합니다.  

<a class="btn primary small round lowercase" id="btnSetShapeOrderID">도형 표시하기</a>

```js
gridView.setColumnProperty("OrderID", "renderer", {type:"shape"});

gridView.setColumnProperty("OrderID", "styles", {
    figureBackground: "#ff008800",
    figureName: "ellipse",
    iconLocation: "right",
    paddingRight: 6
});
```


버튼 클릭시 `CustomerID` 컬럼에 값에 따른 동적으로 도형을 표시합니다.  

<a class="btn primary small round lowercase" id="btnSetShapeCustomerID">도형 표시하기</a>

```js
gridView.setColumnProperty("CustomerID", "renderer", {type:"shape"});

gridView.setColumnProperty("CustomerID", "dynamicStyles", [{
    criteria: "(value = 'WARTH') or (value = 'HILAA')",
    styles: {
        figureBackground: "#ff0000ff",
        figureName: "diamond"
    }
}, {
    criteria: "value = 'VINET'",
    styles: "figureBackground=#ffffcc00;figureName=plus"
}, {
    criteria: "value = 'TOMSP'",
    styles: "figureBackground=#ffcccc00;figureName=ellipse"
}, {
    criteria: "value = 'HANAR'",
    styles: {
        figureBackground: "#ff008800",
        figureName: "minus",
        iconLocation: "right",
        paddingRight: 6
    }
}, {
    criteria: "value = 'HUNGO'",
    styles: "figureBackground=#ff2ffc2f;figureBorder=#ffaaaaaa;figureName=equal"
}, {
    criteria: "value = 'SUPRD'",
    styles: "figureBackground=#ffff44f5;figureName=rectangle"
}]);
```

버튼 클릭시 `UnitPrice` 컬럼에 숫자 값에 따른 도형을 표시합니다.  

<a class="btn primary small round lowercase" id="btnSetShapeUnitPrice">도형 표시하기</a>

```js
gridView.setColumnProperty("UnitPrice", "renderer", {type:"shape"});

gridView.setColumnProperty("UnitPrice", "dynamicStyles", [{
    criteria: "value < 20",
    styles: "figureBackground=#ff0000ff;foreground=#ff0000ff;figureName=itriangle"
}, {
    criteria: "value < 10",
    styles: "background=#110000ff;figureBackground=#ff0000ff;foreground=#ff0000ff;figureName=downarrow"
}, {
    criteria: "value >= 20",
    styles: "figureBackground=#ffff0000;foreground=#ffff0000;figureName=triangle"
}, {
    criteria: "value > 80",
    styles: "background=#11ff0000;figureBackground=#ffff0000;foreground=#ffff0000;figureName=uparrow"
}]);
```

<script>
$('#btnSetShapeOrderID').click(function() {
	gridView.setColumnProperty("OrderID", "renderer", {type:"shape"});

	gridView.setColumnProperty("OrderID", "styles", {
	    figureBackground: "#ff008800",
	    figureName: "ellipse",
	    iconLocation: "right",
	    paddingRight: 6
	});
});

$('#btnSetShapeCustomerID').click(function() {
	gridView.setColumnProperty("CustomerID", "renderer", {type:"shape"});
	gridView.setColumnProperty("CustomerID", "dynamicStyles", [{
	    criteria: "(value = 'WARTH') or (value = 'HILAA')",
	    styles: {
	        figureBackground: "#ff0000ff",
	        figureName: "diamond"
	    }
	}, {
	    criteria: "value = 'VINET'",
	    styles: "figureBackground=#ffffcc00;figureName=plus"
	}, {
	    criteria: "value = 'TOMSP'",
	    styles: "figureBackground=#ffcccc00;figureName=ellipse"
	}, {
	    criteria: "value = 'HANAR'",
	    styles: {
	        figureBackground: "#ff008800",
	        figureName: "minus",
	        iconLocation: "right",
	        paddingRight: 6
	    }
	}, {
	    criteria: "value = 'HUNGO'",
	    styles: "figureBackground=#ff2ffc2f;figureBorder=#ffaaaaaa;figureName=equal"
	}, {
	    criteria: "value = 'SUPRD'",
	    styles: "figureBackground=#ffff44f5;figureName=rectangle"
	}])
});

$('#btnSetShapeUnitPrice').click(function() {
	gridView.setColumnProperty("UnitPrice", "renderer", {type:"shape"});

	gridView.setColumnProperty("UnitPrice", "dynamicStyles", [{
		criteria: "value < 20",
	    styles: "figureBackground=#ff0000ff;foreground=#ff0000ff;figureName=itriangle"
	}, {
	    criteria: "value < 10",
	    styles: "background=#110000ff;figureBackground=#ff0000ff;foreground=#ff0000ff;figureName=downarrow"
	}, {
	    criteria: "value >= 20",
	    styles: "figureBackground=#ffff0000;foreground=#ffff0000;figureName=triangle"
	}, {
	    criteria: "value > 80",
	    styles: "background=#11ff0000;figureBackground=#ffff0000;foreground=#ffff0000;figureName=uparrow"
	}]);
});
</script>