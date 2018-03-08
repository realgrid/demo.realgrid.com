#### 피벗 프로그레그스바

피벗 데이터 로드 시 진행 상태를 [프로그레스바](http://help.realgrid.com/pivotApi/types/DisplayOptions/)로 표시합니다.

<a class="btn primary small round lowercase" id="btnDrawView">다시 그리기</a>

```js
pivot.setDisplayOptions({showProgress:true})
```

<script>
$('#btnDrawView').click(function() {
	pivot.drawView()
});
</script>