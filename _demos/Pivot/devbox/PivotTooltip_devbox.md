#### 툴팁 표시 설정

피벗에서 값 셀과 라빌 셀에 각각 툴팁을 표시할 수 있습니다.
[setDisplayOptions()](http://help.realgrid.com/pivotApi/types/DisplayOptions/){:target="_blank"}

<a class="btn primary small round lowercase" id="btnSetTooltip">값 툴팁 표시</a>

```js
pivot.setDisplayOptions({
	showTooltip:true
});
```

<a class="btn primary small round lowercase" id="btnSetLabelTooltip">라벨 툴팁 표시</a>

```js
pivot.setDisplayOptions({
	showLabelTooltip:true
});
```

툴팁은 마우스 포인터가 셀에 일정 시간 머무르면 표시하도록 되어있습니다. 기본값은 200(millisecond)입니다.<br/>
<a class="btn primary small round lowercase" id="btnSetTooltipDelay">툴팁 지연시간 1초로 변경</a>

```js
pivot.setDisplayOptions({
	tooltipDelay: 1000
});
```

#### 툴팁 내용 커스트마이징

피벗에서는 툴팁의 내용을 개발자가 변경할 수 있도록 값 셀의 [onTooltip](http://help.realgrid.com/pivotApi/RealPivot/onTooltip/){:target="_blank"} 콜백 과 라벨 셀의 [onLabelTooltip](http://help.realgrid.com/pivotApi/RealPivot/onLabelTooltip/) 콜백을 제공합니다.

<a class="btn primary small round lowercase" id="btnSetCallback">툴팁 콜백 지정</a>

```js
pivot.onTooltip = function (view, index, s) {
    return "사용자 지정 툴팁입니다."; 
}
pivot.onLabelTooltip = function (view, index, s) {
    return "사용자 지정 라벨 툴팁입니다."
}
```

<script>
	$('#btnSetTooltip').click(function() {
		pivot.setDisplayOptions({showTooltip:true});
    });
	$('#btnSetLabelTooltip').click(function() {
		pivot.setDisplayOptions({showLabelTooltip:true});
    });
	$('#btnSetTooltipDelay').click(function() {
		pivot.setDisplayOptions({tooltipDelay: 1000});
    });
	$('#btnSetCallback').click(function() {
		pivot.onTooltip = function (view, index, s) {
		    return "사용자 지정 툴팁입니다."; 
		}
		pivot.onLabelTooltip = function (view, index, s) {
		    return "사용자 지정 라벨 툴팁입니다."
		}
    });
</script>