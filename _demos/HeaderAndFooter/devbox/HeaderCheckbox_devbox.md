#### 컬럼 헤더 체크박스 위치

- `checkLocation`: 헤더 체크박스의 위치를 지정합니다.

```js
var columns = [{
    "name": "OrderDate",
    "fieldName": "OrderDate",
    "width": "130",
    "styles": {
        "textAlignment": "center"
    },
    "header": {
        "text": "Order Date",
        "checkLocation": "left"
    },
    "checkded": "true"
}
```

#### 컬럼 헤더 체크 선택
- `column.checked`: 컬럼 헤더에 체크를 선택합니다.

<a class="btn primary small round lowercase" id="btnSetColumnUnChecked">헤더 체크 해제하기</a>
<a class="btn primary small round lowercase" id="btnSetColumnChecked">헤더 체크 선택하기</a>
```js
  var checkColumn = gridView.columnByName("GroupIds");
  checkColumn.checked = true;
  gridView.setColumn(checkColumn);
```

<script>

  $('#btnSetColumnChecked').click(function() {
    var checkColumn = gridView.columnByName("GroupIds");
    checkColumn.checked = true;
    gridView.setColumn(checkColumn);    
  });

  $('#btnSetColumnUnChecked').click(function() {
    var unCheckColumn = gridView.columnByName("GroupIds");
    unCheckColumn.checked = false;
    gridView.setColumn(unCheckColumn);
  });

</script>
