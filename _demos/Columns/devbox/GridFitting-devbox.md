#### 그룹컬럼 보기 
버튼 클릭으로 그룹 컬럼이 표시된 상태에서 컬럼 너비 자동 조정 기능을 적용시켜 보시기 바랍니다.  
버튼 클릭 시 그룹컬럼이 그리드에 표시됩니다. 

<a class="btn primary small round lowercase" id="btnGroupColumnVisible">그룹컬럼 보이기</a>

```js
var groupVisible = gridView.getColumnProperty("GroupOrder","visible");

if(groupVisible){
  gridView.setColumnPropert("GroupOrder", "visible", false);
} else {
  gridView.setColumnPropert("GroupOrder","visible", true);
}
```

#### none
채우기를 하지 않습니다.

<a class="btn primary small round lowercase" id="btnNone">none</a>

```js
gridView.setDisplayOptions({
  fitStyle: "none"
});
```

#### even
컬럼 전체의 너비가 그리드 영역보다 작으면 각 컬럼의 너비를 width 속성값에 맞춰 그리드의 너비에 맞게 비례적으로 배분합니다.

<a class="btn primary small round lowercase" id="btnEven">even</a>

```js
gridView.setDisplayOptions({
  fitStyle: "even"
});
```
#### evenFill
컬럼 전체 너비와 상관없이 각 컬럼의 너비를 width 속성값에 맞춰 그리드의 너비에 맞게 비례적으로 항상 배분합니다.

<a class="btn primary small round lowercase" id="btnEvenFill">evenFill</a>

```js
gridView.setDisplayOptions({
  fitStyle: "evenFill"
});
```

#### fill
컬럼 전체의 너비가 그리드 영역보다 작으면 fillWidth 값이 0 이하인 컬럼은 손대지 않고, 0보다 큰 컬럼들을 fillWidth 비율대로 배분합니다. 아래 예제에서는 "Customer ID", "Employee ID" 컬럼들만 fillWidth 값이 1로 설정됐습니다.

<a class="btn primary small round lowercase" id="btnFill">fill</a>

```js
gridView.setDisplayOptions({
  fitStyle: "fill"
});
```

<script>

$("#btnNone").click(function() { 
  gridView.setDisplayOptions({
    fitStyle: "none"
  });
});

$("#btnEven").click(function() { 
  gridView.setDisplayOptions({
    fitStyle: "even"
  });
});

$("#btnEvenFill").click(function() { 
  gridView.setDisplayOptions({
    fitStyle: "evenFill"
  });
});

$("#btnFill").click(function() { 
  gridView.setDisplayOptions({
    fitStyle: "fill"
  });
});

$("#btnGroupColumnVisible").click(function() { 
  var groupVisible = gridView.getColumnProperty("GroupOrder","visible");

  if(groupVisible){
    gridView.setColumnProperty("GroupOrder", "visible", false);
    document.getElementById("btnGroupColumnVisible").innerHTML = "그룹컬럼 보이기"
  } else {
    gridView.setColumnProperty("GroupOrder","visible", true);
    document.getElementById("btnGroupColumnVisible").innerHTML = "그룹컬럼 숨기기"
  }
});
</script>

