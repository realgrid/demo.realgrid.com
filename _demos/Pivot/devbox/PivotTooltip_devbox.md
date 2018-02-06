#### 피벗 툴팁 설정

피벗 툴팁 적용 버튼 클릭 시 pivot 화면에 툴팁 기능을 적용시킵니다.

<a class="btn primary small round lowercase" id="btnSetPivotTooltip">피벗 툴팁 적용</a>

```js
pivot.setDisplayOptions({showTooltip:true})
```


<script>
	$('#btnSetPivotTooltip').click(function() {
		pivot.setDisplayOptions({showTooltip:true})
    });
</script>