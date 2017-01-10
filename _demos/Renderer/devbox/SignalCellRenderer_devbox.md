#### 시그널 렌더러 표시 방법

`SignalCellRenderer`를 설정 해보겠습니다.

* 시그널을 표시하기 위해서는 renderer의 type을 `signal`로 설정합니다.
* 시그널을 표시하기 위한 바의 개수를 지정합니다.

```js
renderer: {
    type: "signal",
    barCount: 10
}
```

다음으로 시그널의 색상과 신호바의 세기를 설정합니다.

* `figureBackground`로 색상 또한 다양하게 설정할 수 있습니다.
* `figureState`는 신호바의 세기로 사용됩니다.  
* (figureState가 3이면 세 개의 시그널 바에 신호가 표시됩니다.)

```js
styles: {
    figureBackground: "#ffff00ff",
    figureState: "value"
}
```

#### 시그널 렌더러 표시하기

버튼 클릭시 `Employee ID 2` 컬럼에 기본 설정의 시그널을 표시합니다.  

<a class="btn primary small round lowercase" id="btnSignalEmployee">시그널 표시하기</a>

```js
gridView.setColumnProperty("EmployeeID2", "renderer", {type:"signal", barCount:10});

gridView.setColumnProperty("EmployeeID2", "styles", {figureState: "value"});
```

버튼 클릭시 `Quantity 2` 컬럼에 값에 따른 동적 시그널을 표시합니다.  

<a class="btn primary small round lowercase" id="btnSignalQuantity">시그널 표시하기</a>

```js
gridView.setColumnProperty("Quantity2", "renderer", {type:"signal", barCount:20});

gridView.setColumnProperty("Quantity2", "dynamicStyles", [
    {
        criteria: "value < 10",
        styles: "figureBackground=#66ffff00;figureState=2"
    }, {
        criteria: "value >= 10",
        styles: "figureBackground=#66ff0000;figureState=4"
    }, {
        criteria: "value >= 40",
        styles: "figureBackground=#88ff0000;figureState=6"
    }, {
        criteria: "value >= 60",
        styles: "figureBackground=#aa0000ff;figureState=12"
    }, {
        criteria: "value >= 80",
        styles: "figureBackground=#aa0000ff;figureState=15"
    }, {
        criteria: "value >= 100",
        styles: "figureBackground=#ff0000ff;figureState=20"
    }
]);
```

<script>
$('#btnSignalEmployee').click(function() {
	gridView.setColumnProperty("EmployeeID2", "renderer", {type:"signal", barCount:10});

	gridView.setColumnProperty("EmployeeID2", "styles", {figureState: "value"});
});

$('#btnSignalQuantity').click(function() {
	gridView.setColumnProperty("Quantity2", "renderer", {type:"signal", barCount:20});

	gridView.setColumnProperty("Quantity2", "dynamicStyles", [
	    {
	        criteria: "value < 10",
	        styles: "figureBackground=#66ffff00;figureState=2"
	    }, {
	        criteria: "value >= 10",
	        styles: "figureBackground=#66ff0000;figureState=4"
	    }, {
	        criteria: "value >= 40",
	        styles: "figureBackground=#88ff0000;figureState=6"
	    }, {
	        criteria: "value >= 60",
	        styles: "figureBackground=#aa0000ff;figureState=12"
	    }, {
	        criteria: "value >= 80",
	        styles: "figureBackground=#aa0000ff;figureState=15"
	    }, {
	        criteria: "value >= 100",
	        styles: "figureBackground=#ff0000ff;figureState=20"
	    }
	]);
});
</script>