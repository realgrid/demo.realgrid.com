#### 왼쪽 열 고정
[FixedOptions](http://help.realgrid.com/api/types/FixedOptions/)의 속성중 rowCount를 지정하여 최상위 행 중 하나 이상의 행을 스크롤에서 제외시킬 수 있습니다.  
<a class="btn primary small round lowercase" id="btnSetRowCount">행 고정</a>

```js
gridView.setFixedOptions({
  rowCount: 2
});
```

<script>

  $('#btnSetRowCount').click(function() {
    gridView.setFixedOptions({
      rowCount: 2
    });
  });

</script>
