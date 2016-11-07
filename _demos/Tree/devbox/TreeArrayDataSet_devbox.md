
이 함수에는 트리를 구성하기 위해 아래와 같은 인자를 포함하고 있습니다.

- `rows`: 트리 데이터
- `treeField`: 트리 구조를 담고 있는 필드명
- `needSorting`: `treeField`로 정렬을 다시 할 것인지 여부
- `childrenField`: 자식 행이 있는지 지정하는 필드명
- `iconField`: 아이콘 인덱스 필드명

[setRows()](http://help.realgrid.com/api/TreeDataProvider/setRows/){:target='_blank'}함수를 호출하는 샘플 코드를 작성해 보겠습니다.

```js
treeDataProvider.setRows(data,
  "tree",
  true,
  "",
  "icon");
```

TreeView는 GridView와 달리 몇 가지 제약사항이 있습니다.

- RowGrouping: **트리는 그룹핑을 지원하지 않습니다.**
- Filtering: **부모 행이 필터에 의해 제외되면 자식 행들 역시 제외됩니다.**
- Sorting: **정렬시 계층 구조를 유지한채 자식들만 정렬됩니다.**
