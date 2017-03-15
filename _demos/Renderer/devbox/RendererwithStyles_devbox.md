#### 렌더러 추가
 
[addCellRenderers](http://help.realgrid.com/api/GridBase/addCellRenderers/)함수로 렌더러 정보들을 미리 추가합니다.

컬럼 동적 스타일에 추가한 renderer 값을 이용하면, 같은 컬럼에서 값에 따라 다른 렌더러의 `id`를 사용하여 셀을 표시할 수 있습니다.

<a class="btn primary small round lowercase" id="btnAddCellRenderers">렌더러 정보 추가</a>

```js
gridView.addCellRenderers([{
    "id": "bar01",
    "type": "bar"
}, {
    "id": "bar02",
    "type": "bar",
    "maximum": 100,
    "showLabel": false
}, {
    "id": "check01",
    "type": "check",
    "editable": true,
    "startEditOnClick": true,
    "trueValues": "True",
    "falseValues": "False",
    "labelPosition": "right"				
}, {
    "id": "shape01",
    "type": "shape"
}, {
    "id": "signal01",
    "type": "signal",
    "barCount": 10,
    "minimum": 0,
    "maximum": 100
}, {
    "id": "signal02",
    "type": "signal",
    "barCount": 20,
    "minimum": 0,
    "maximum": 100
}]);
```

#### 한 컬럼에 다양한 렌더러 사용

`addCellRenderers`함수로 추가한 renderer의 `id` 값을 renderer에 설정해서 컬럼에 여러가지 렌더러를 동적으로 사용할 수 있습니다.  

`UnitPrice2`, `Quantity2` 컬럼에 적용된 `signal`, `bar`, `shape` 렌더러를 확인해 보세요.

<a class="btn primary small round lowercase" id="btnSetRendererUnitPrice2">렌더러 정보 추가</a>

```js
gridView.setColumnProperty("UnitPrice2", "dynamicStyles", [{
    "criteria": "value >= 0",
    "styles": {
        "renderer": "signal01",
        "figureBackground": "#ffffff7f",
        "figureState": "value"
    }
}, {
    "criteria": "value >= 30",
    "styles": {
        "renderer": "signal02",
        "figureBackground": "#ffd4ff55",
        "figureState": "value"
    }
}, {
    "criteria": "value >= 60",
    "styles": {
        "renderer": "bar01",
        "figureBackground": "#ffd4ff55",
        "figureSize": "30%",
        "figureState": "value"
    }
}, {
    "criteria": "value >= 90",
    "styles": {
        "renderer": "shape01",
        "figureName": "ellipse",
        "figureBackground": "#ffff0000",
        "figureSize": 12
    }
}]);
```

#### 체크박스의 체크여부에 따른 렌더러 적용

`체크박스에 체크된 행`에 shape renderer를 적용 합니다.

`UnitPrice1`, `Quantity1` 컬럼에 체크 시 적용되는 `shape` 렌더러를 확인해 보세요.

<a class="btn primary small round lowercase" id="btnSetCheckRenderer">체크시 렌더러 적용</a>

```js
gridView.setColumnProperty("UnitPrice1", "dynamicStyles", [{
    "criteria": "checked", //체크 시 styles 적용
    "styles": {
        "renderer": "shape01"
    }
}, {
    "criteria": "(value < 20) and (checked)",
    "styles": "figureBackground=#ff0000ff;foreground=#ff0000ff;figureName=itriangle"
}, {
    "criteria": "(value < 10) and (checked)",
    "styles": "figureBackground=#ff0000ff;foreground=#ff0000ff;figureName=downarrow"
}, {
    "criteria": "(value >= 20) and (checked)",
    "styles": "figureBackground=#ffff0000;foreground=#ffff0000;figureName=triangle"
}, {
    "criteria": "(value > 80) and (checked)",
    "styles": "figureBackground=#ffff0000;foreground=#ffff0000;figureName=uparrow"
}]);
```



<script>
$('#btnAddCellRenderers').click(function() {
	gridView.addCellRenderers([{
	    "id": "bar01",
	    "type": "bar"
	}, {
	    "id": "bar02",
	    "type": "bar",
	    "maximum": 100,
	    "showLabel": false
	}, {
	    "id": "check01",
	    "type": "check",
	    "editable": true,
	    "startEditOnClick": true,
	    "trueValues": "True",
	    "falseValues": "False",
	    "labelPosition": "right"				
	}, {
	    "id": "shape01",
	    "type": "shape"
	}, {
	    "id": "signal01",
	    "type": "signal",
	    "barCount": 10,
	    "minimum": 0,
	    "maximum": 100
	}, {
	    "id": "signal02",
	    "type": "signal",
	    "barCount": 20,
	    "minimum": 0,
	    "maximum": 100
	}]);
});

$('#btnSetRendererUnitPrice2').click(function() {
	gridView.setColumnProperty("UnitPrice2", "dynamicStyles", [{
	    "criteria": "value >= 0",
	    "styles": {
	        "renderer": "signal01",
	        "figureBackground": "#ffffff7f",
	        "figureState": "value"
	    }
	}, {
	    "criteria": "value >= 30",
	    "styles": {
	        "renderer": "signal02",
	        "figureBackground": "#ffd4ff55",
	        "figureState": "value"
	    }
	}, {
	    "criteria": "value >= 60",
	    "styles": {
	        "renderer": "bar01",
	        "figureBackground": "#ffd4ff55",
	        "figureSize": "50%",
	        "figureState": "value"
	    }
	}, {
	    "criteria": "value >= 90",
	    "styles": {
	        "renderer": "shape01",
	        "figureName": "ellipse",
	        "figureBackground": "#ffff0000",
	        "figureSize": 12
	    }
	}]);

    gridView.setColumnProperty("Quantity2", "dynamicStyles", [{
	    "criteria": "value >= 0",
	    "styles": {
	        "renderer": "signal01",
	        "figureBackground": "#ffffff7f",
	        "figureState": "value"
	    }
	}, {
	    "criteria": "value >= 30",
	    "styles": {
	        "renderer": "signal02",
	        "figureBackground": "#ffd4ff55",
	        "figureState": "value"
	    }
	}, {
	    "criteria": "value >= 60",
	    "styles": {
	        "renderer": "bar01",
	        "figureBackground": "#ffd4ff55",
	        "figureSize": "30%",
	        "figureState": "value"
	    }
	}, {
	    "criteria": "value >= 90",
	    "styles": {
	        "renderer": "shape01",
	        "figureName": "ellipse",
	        "figureBackground": "#ffff0000",
	        "figureSize": 12
	    }
	}]);
});

$('#btnSetCheckRenderer').click(function() {
	gridView.setColumnProperty("UnitPrice1", "dynamicStyles", [{
	    "criteria": "checked",
	    "styles": {
	        "renderer": "shape01",
	        "figureBackground": "#ffffcc00",
	        "foreground": "#ff0000ff",
	        "figureName":"star",
	        "figureSize": 15
	    }
	}, {
        "criteria": "(value < 20) and (checked)",
        "styles": "figureBackground=#ff0000ff;foreground=#ff0000ff;figureName=itriangle"
    }, {
        "criteria": "(value < 10) and (checked)",
        "styles": "figureBackground=#ff0000ff;foreground=#ff0000ff;figureName=downarrow"
    }, {
        "criteria": "(value >= 20) and (checked)",
        "styles": "figureBackground=#ffff0000;foreground=#ffff0000;figureName=triangle"
    }, {
        "criteria": "(value > 80) and (checked)",
        "styles": "figureBackground=#ffff0000;foreground=#ffff0000;figureName=uparrow"
    }]);

	gridView.setColumnProperty("Quantity1", "dynamicStyles", [{
	    "criteria": "checked",
	    "styles": {
	        "renderer": "shape01"
	    }
	}, {
        "criteria": "(value < 20) and (checked)",
        "styles": "figureBackground=#ff0000ff;foreground=#ff0000ff;figureName=itriangle"
    }, {
        "criteria": "(value < 10) and (checked)",
        "styles": "figureBackground=#ff0000ff;foreground=#ff0000ff;figureName=downarrow"
    }, {
        "criteria": "(value >= 20) and (checked)",
        "styles": "figureBackground=#ffff0000;foreground=#ffff0000;figureName=triangle"
    }, {
        "criteria": "(value > 80) and (checked)",
        "styles": "figureBackground=#ffff0000;foreground=#ffff0000;figureName=uparrow"
    }]);
});
</script>