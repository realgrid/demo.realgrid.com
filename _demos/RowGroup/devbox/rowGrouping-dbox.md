인디케이터 `displayValue` 속성 변경 하기

*displayValue*
* `none`: 값을 표시 하지 않습니다.
* `index`: 1부터 시작하여 표시합니다. (정렬에 무관하게 1번부터 시작)
* `row`: Row의 고유번호를 표시합니다. (정렬에 따라서 섞여서 표시)

<a class="btn primary small round lowercase" id="btnSetDisplayValueNone">none</a>
```js
gridView.setIndicator({
  displayValue: "none"  
});
```
<a class="btn primary small round lowercase" id="btnSetDisplayValueIndex">Index</a>
```js
gridView.setIndicator({
  displayValue: "index"  
});
```
<a class="btn primary small round lowercase" id="btnSetDisplayValueRow">Row</a>
```js
gridView.setIndicator({
  displayValue: "row"  
});
```

<a class="btn primary small round lowercase" id="btnSetDisplayValueNone2">none</a>
<a class="btn primary small round lowercase" id="btnSetDisplayValueIndex2">Index</a>
<a class="btn primary small round lowercase" id="btnSetDisplayValueRow2">Row</a>

```js
gridView.setIndicator({
  displayValue: "none"  
});

gridView.setIndicator({
  displayValue: "index"  
});

gridView.setIndicator({
  displayValue: "row"  
});
```

<script>

  $('#btnSetDisplayValueNone').click(function() {
    gridView.setIndicator({
      displayValue: "none"  
    });
  });

  $('#btnSetDisplayValueIndex').click(function() {
    gridView.setIndicator({
      displayValue: "index"  
    });
  });

  $('#btnSetDisplayValueRow').click(function() {
    gridView.setIndicator({
      displayValue: "row"  
    });
  });
</script>
