
#### 트리뷰 구현 방법

트리뷰(TreeView)는 그리드뷰(GridView)의 데이터 행 들을 계층 구조로 표현 할 수 있습니다.
즉, 트리 형식의 데이터를 표현할 수 있도록 만들어진 컨트롤입니다.

트리뷰에 계층구조를 표현하기 위한 몇 가지 방법을 소개 합니다.
데이터 유형에 따라 각기 다른 함수를 사용합니다. 이 함수들은 `TreeDataProvider`객체에 구현되어 있습니다.

- [트리 구현 - Array 데이터]({{ "/Tree/TreeArrayDataSet/" | prepend: site.baseurl }})
  - [`setRows()`](http://help.realgrid.com/api/TreeDataProvider/setRows/)

- [트리 구현 - JSON 데이터]({{ "/Tree/TreeJsonDataSet/" | prepend: site.baseurl }})
  - [`setJsonRows()`](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)
  - [`fillJsonData()`](http://help.realgrid.com/api/TreeDataProvider/fillJsonData/)

- [트리 구현 - XML 데이터]({{ "/Tree/TreeXmlDataSet/" | prepend: site.baseurl }})
  - [`setXmlRows()`](http://help.realgrid.com/api/TreeDataProvider/setXmlRows/)
  - [`fillXmlData()`](http://help.realgrid.com/api/TreeDataProvider/fillXmlData/)

- [트리 구현 - CSV 데이터]({{ "/Tree/TreeCsvDataSet/" | prepend: site.baseurl }})
  - [`fillCsvData()`](http://help.realgrid.com/api/TreeDataProvider/fillCsvData/)

- [jQuery ajax() 이용하기]({{ "/Tree/TreeLoadData/" | prepend: site.baseurl }})
  - jQuery ajax()함수를 이용해 원격 데이터를 트리뷰(TreeView)에 로드 하는 방법을 설명합니다.

RealGrid 튜토리얼에 계층 구조 표현을 위한 데이터 구조에 대해 좀더 자세히 다루고 있는 문서들이 있습니다. 아래 링크를 참조하세요.

  - [B9-1 배열형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-1/)
  - [B9-2 JSON형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-2/)
  - [B9-3 TreeView의 ItemModel 이해하기](http://help.realgrid.com/tutorial/b9-3/)

#### 트리뷰의 제약사항

트리뷰(TreeView)는 그리드뷰(GridView)와 달리 몇 가지 제약사항이 있습니다.

- RowGrouping: **트리는 그룹핑을 지원하지 않습니다.**
- Filtering: **부모 행이 필터로 제외되면 자식 행들 역시 제외됩니다.**
- Sorting: **정렬시 계층 구조를 유지한 채 자식들만 정렬됩니다.**
- 트리 컬럼: **트리가 보여지는 컬럼은 항상 첫 번째 컬럼 입니다.**
