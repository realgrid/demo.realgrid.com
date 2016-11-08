
#### 트리뷰 구현 방법

TreeView는 GridView의 각 행들이 계층구조를 갖고 트리형식으로 표현할 수 있도록 만들어진 컨트롤입니다.


TreeView에 계층구조를 표현하기 위해 데이터 유형에 따라 몇 가지 방법으로 구현이 가능하며,
`TreeDataProvider`에는 트리 구현을 위한 함수가 마련되어 있습니다.

- [트리 구현 - 배열형 데이터]({{ "/Tree/TreeArrayDataSet/" | prepend: site.baseurl }})
  - [setRows()](http://help.realgrid.com/api/TreeDataProvider/setRows/)함수를 이용한 트리구현
- [트리 구현 - JSON 데이터]({{ "/Tree/TreeJsonDataSet/" | prepend: site.baseurl }})
  - [setJsonRows()](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)
- [트리 구현 - XML 데이터]({{ "/Tree/TreeXmlDataSet/" | prepend: site.baseurl }})
  - [setXmlRows()](http://help.realgrid.com/api/TreeDataProvider/setXmlRows/)
- [트리 구현 - loadData()함수]({{ "/Tree/TreeLoadData/" | prepend: site.baseurl }})
  - [loadData()](http://help.realgrid.com/api/TreeDataProvider/loadData/)

#### 트리뷰의 제약사항

TreeView는 GridView와 달리 몇 가지 제약사항이 있습니다.

- RowGrouping: **트리는 그룹핑을 지원하지 않습니다.**
- Filtering: **부모 행이 필터로 제외되면 자식 행들 역시 제외됩니다.**
- Sorting: **정렬시 계층 구조를 유지한 채 자식들만 정렬됩니다.**
