
#### CSV 트리 데이터

아래 코드는 트리뷰(TreeView)를 구현하기 위한 CSV 데이터 구조 입니다.

```js
var data =
  '0, 1, 경기도\n'+
  '0, 1.1, 경기도, 성남시\n'+
  '0, 1.1.1, 경기도, 성남시, 분당구\n'+
  '0, 1.2, 경기도, 수원시\n'+
  '0, 1.2.2, 경기도, 수원시, 팔달구\n'+
  '0, 1.2.1, 경기도, 수원시, 영통구\n'+
  '0, 1.1.2, 경기도, 성남시, 수정구\n'+
  '0, 1.3, 경기도, 안양시\n'+
  '0, 1.4, 경기도, 의정부시\n'+
  '0, 1.5, 경기도, 김포시\n';
```

#### CSV 데이터로 트리 구현

`CSV 데이터`로 트리를 구현하기 위해서 아래 함수를 사용할 수 있습니다.

- [TreeDataProvider.fillCsvData()](http://help.realgrid.com/api/TreeDataProvider/fillCsvData/)

함수를 호출하는 샘플 코드를 작성해 보겠습니다.

<a class="btn primary small round lowercase" id="fillCsvData">fillCsvData()로 트리 구현</a>

```js
// CSV 데이터 입력하기
treeDataProvider.fillCsvData(data,
  {
    tree:"tree",
    icon:"icon",
    sorting:true,
    quoted:false,
    start:1
  });
treeView.expandAll();
```

#### 트리 구현을 위한 CSV 데이터 계층 구조

CSV 데이터의 계층 구조는 Array 데이터의 방식과 거의 동일하게 `트리코드`에 해당 하는 필드를
옵션에 지정해 주는 방식입니다.

`트리코드(tree code)`는 바로 전에 입력된 트리코드와 비교하여 `문자열의 포함 여부` 또는 `문자열의 갯수`를
기준으로 노드의 깊이(Level)를 판단 합니다. 트리코드에 대한 자세한 설명은
\[[B9-3 TreeView의 ItemModel 이해하기](http://help.realgrid.com/tutorial/b9-3/)\]를
참조하세요.


아래는 [TreeDataProvider.fillCsvData()](http://help.realgrid.com/api/TreeDataProvider/fillCsvData/)함수의 정의 입니다.

```js
function fillCsvData(data, options) {}
```

이 함수의 두 번째 인자인 `options` 즉 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)의
`tree`속성의 값에 `트리코드`를 지정하면 됩니다.

즉, 데모 데이터에서 두 번째 필드의 값에 해당하는 데이터가 `트리코드`이며 이 필드의 이름인 `tree`를 해당
옵션의 속성 값에 넣어 주는 것으로 계층 구조를 만들수 있습니다.

또, Array 데이터와 마찬 가지로 계층 구조를 `트리코드`로 만들다 보니 최초 정렬 순서도 중요하기 때문에
옵션에서 `sorting` 속성의 값을 이용해 정렬여부를 결정 할 수도 있습니다.

RealGrid 튜토리얼에 계층 구조 표현을 위한 데이터 구조에 대해 좀더 자세히 다루고 있는 문서들이 있습니다.
아래 링크를 참조하세요.

  - [B9-1 배열형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-1/)
  - [B9-2 JSON형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-2/)
  - [B9-3 TreeView의 ItemModel 이해하기](http://help.realgrid.com/tutorial/b9-3/)

{% include_relative devbox/TreeIcon.md %}

{% comment %} ----------------- DEVBOX SCRIPT --------------- {% endcomment %}
<script>
  var data =
  '0, 1, 경기도\n'+
  '0, 1.1, 경기도, 성남시\n'+
  '0, 1.1.1, 경기도, 성남시, 분당구\n'+
  '0, 1.2, 경기도, 수원시\n'+
  '0, 1.2.2, 경기도, 수원시, 팔달구\n'+
  '0, 1.2.1, 경기도, 수원시, 영통구\n'+
  '0, 1.1.2, 경기도, 성남시, 수정구\n'+
  '0, 1.3, 경기도, 안양시\n'+
  '0, 1.4, 경기도, 의정부시\n'+
  '0, 1.5, 경기도, 김포시\n';

  $('#fillCsvData').click(function() {
    treeDataProvider.fillCsvData(data,
      {
        tree:"tree",
        icon:"icon",
        sorting:true,
        quoted:false,
        start:1
      });
    treeView.expandAll();
  });

  $('#clearRows').click(function() {
    treeDataProvider.clearRows();
  });
</script>
