컬럼의 `equalBlank` 속성을 `true`로 지정하면, 바로 직전 행의 값과 일치하는 셀은 그리지 않고 비웁니다.

```js
var columns = [{
...
},{
  name: "CustomerID",
  fieldName: "CustomerID",
  type: "data",
  width: "130",
  equalBlank: true,
  styles: {
    textAlignment: "center"
  },
  header: {
    text: "Customer ID"
  }
},{
...
}];
grid.setColumns(columns);
```

<a class="btn primary small round lowercase" id="btnEqualBlankTrue">true</a>

```js
gridView.setColumnProperty("CustomerID", "equalBlank", true);
```

<a class="btn primary small round lowercase" id="btnEqualBlankFalse">false</a>

```js
gridView.setColumnProperty("CustomerID", "equalBlank", false);
```

<script>

  $('#btnEqualBlankTrue').click(function() {
    gridView.setColumnProperty("CustomerID", "equalBlank", true);
  });

  $('#btnEqualBlankFalse').click(function() {
    gridView.setColumnProperty("CustomerID", "equalBlank", false);
  });

</script>