#### 피벗 프로그레그

피벗 데이터 로드 시 진행 상태를 표시합니다.

<a class="btn primary small round lowercase" id="btnDrawView">다시 그리기</a>

```js
pivot.setDisplayOptions({showProgress:true})
```


<script>
$('#btnDrawView').click(function() {
	pivot.drawView()
});
</script>