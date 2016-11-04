TreeView는 GridView의 각 행들이 계층구조를 갖고 트리형식으로 표현할 수 있도록 만들어진 컨트롤입니다.


TreeView에 계층구조를 표현하기 위해 데이터 유형에 따라 세가지 방법으로 구현이 가능하며,
`TreeDataProvider`에는 세 가지 방법에 대한 함수가 마련되어 있습니다. 각 함수에 대한 소개를 위해
각각 별도의 데모페이지가 준비되어 있습니다.

- [setRows()](http://help.realgrid.com/api/TreeDataProvider/setRows/): [트리: 배열형 데이터]({{ "/Tree/Indicator/" | prepend: site.baseurl }})
- [setJsonRows()](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)
- [setXmlRows()](http://help.realgrid.com/api/TreeDataProvider/setXmlRows/)

각 함수에 대한 데모는 각각 다른 페이지에서 설명
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
