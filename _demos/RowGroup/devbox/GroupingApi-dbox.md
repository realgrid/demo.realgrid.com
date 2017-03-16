#### rowGroup API

* `groupBy`: 지정한 필드 개수 만큼의 레벨로 Row Grouping을 실행합니다. 인자로 빈 배열이거나 null을 지정하면 Grouping을 해제합니다.
* `isGrouped`: 그리드가 RowGrouping 인지 확인합니다. (Grouping이면 true를 반환합니다.)
* `isMergedGrouped`: 그리드가 mergeMode 중인지 확인합니다.
* `getGroupFields`: Grouping field의 index값을 순서대로 반환합니다.
* `getGroupFieldNames`: Grouping field의 이름들을 순서대로 반환합니다. orgName을 true로 주면 fieldSet에 정의된 이름으로 반환합니다.
* `getGroupLevels`: 현재 몇 레벨로 Grouping 되었는지를 리턴 합니다.
* `getGroupLevel`: 지정한 필드의 그룹 레벨을 리턴 합니다. 첫번째 그룹 레벨은 1입니다. 그 필드로 그룹핑되지 않았다면 0을 리턴 합니다.
* `getGroupIndex`: 지정한 아이템의 그룹 아이템의 index를 반환합니다.
* `isGroupItem`: 지정한 아이템이 그룹 아이템이면 true를 반환합니다.
* `isParentVisible`: 지정한 아이템의 그룹아이템이 표시되고 있는지를 반환합니다.
* `expandGroup`: 지정한 그룹을 펼칩니다. recursive를 true로 하면 그룹에 포함된 하위그룹 펼쳐집니다. force 를 true로 하면 이미 펼쳐진상태여도 recursive를 true이면 하위그룹들을 펼칩니다.
* `collapseGroup`: 지정한 그룹을 collapse 합니다. recursive를 true로 하면 그룹에 포함된 자손 그룹도 collapse된 상태가 됩니다.
* `expandParent`: 지정한 아이템이 footer인경우 그룹을 펼칩니다.
* `collapseParent`: 지정한 아이템이 row이거나 footer인경우 그룹을 접습니다.


<a class="btn primary small round lowercase" id="btnGroupBy">groupBy</a>
```js
  gridView.groupBy(["OrderID","CustomerID"]);
```
<a class="btn primary small round lowercase" id="btnUnGroupBy">그룹해제</a>
```js
  gridView.groupBy([]);
```
<a class="btn primary small round lowercase" id="btnIsGrouped">isGrouped</a>
```js
  alert(gridView.isGrouped());
```
<a class="btn primary small round lowercase" id="btnIsMergedGrouped">isMergedGrouped</a>
```js
  alert(gridView.isMergedGrouped());
```

<a class="btn primary small round lowercase" id="btnGetGroupFields">getGroupFields</a>
```js
  alert(gridView.getGroupFields());
```

<input type="checkbox" id="chkOrgFieldName" checked="checked"/><label for="chkOrgFieldName">OrgFieldName</label>

<a class="btn primary small round lowercase" id="btnGetGroupFieldNames">getGroupFieldNames</a>

```js
  alert(gridView.getGroupFieldNames($("#chkOrgFieldName").is(":checked")));
```
<script>

  $('#btnGroupBy').click(function() {
    gridView.groupBy(["OrderID","CustomerID"]);
  });

  $('#btnUnGroupBy').click(function() {
    gridView.groupBy([]);
  });
  $('#btnIsGrouped').click(function() {
    alert(gridView.isGrouped());
  });
  $('#btnIsMergedGrouped').click(function() {
    alert(gridView.isMergedGrouped());
  });
  $('#btnGetGroupFields').click(function() {
    alert(gridView.getGroupFields());
  });
  $('#btnGetGroupFieldNames').click(function() {
    alert(gridView.getGroupFieldNames($("#chkOrgFieldName").is(":checked")));
  });
</script>
