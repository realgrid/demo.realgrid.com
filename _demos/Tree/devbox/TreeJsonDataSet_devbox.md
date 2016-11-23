#### JSON 트리 데이터

아래 코드는 트리를 구현하기 위한 JSON형식의 데이터 입니다.

```js
var data = {
  "rows":[
    { "icon":0, "do":"경기도",
      "rows":[
        { "icon":0, "do":"경기도", "si":"성남시",
          "rows":[
            { "icon":0, "do":"경기도", "si":"성남시", "gu":"분당구" },
            { "icon":0, "do":"경기도", "si":"성남시", "gu":"수정구" }
          ]
        },
        { "icon":0, "do":"경기도", "si":"수원시",
          "rows":[
            { "icon":0, "do":"경기도", "si":"수원시", "gu":"팔달구" },
            { "icon":0, "do":"경기도", "si":"수원시", "gu":"영통구" }
          ]
        },
        { "icon":0, "do":"경기도", "si":"안양시" },
        { "icon":0, "do":"경기도", "si":"의정부시" },
        { "icon":0, "do":"경기도", "si":"김포시" }
      ]
    }
  ]
}
```

#### JSON 데이터로 트리 구현

`JSON 데이터`로 트리를 구현하기 위해 아래 두 함수를 사용할 수 있습니다.

- [TreeDataProvider.setJsonRows()](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)
- [TreeDataProvider.fillJsonData()](http://help.realgrid.com/api/TreeDataProvider/fillJsonData/)

먼저 [setJsonRows()](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)
함수를 호출하여 트리를 구현해 보겠습니다.

<a class="btn primary small round lowercase" id="setJsonRows">setJsonRows()로 트리 구현</a>

```js
// setJsonRows()로 트리 구현
treeDataProvider.setJsonRows(data, "rows", "", "icon");
treeView.expandAll();
```

같은 데이터를 [fillJsonData()](http://help.realgrid.com/api/TreeDataProvider/fillJsonData/)
함수를 사용해 트리를 구현해 보겠습니다.

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="fillJsonData">fillJsonData()로 트리 구현</a>

```js
// 데이터 지우기
treeDataProvider.clearRows();

// fillJsonData()로 트리 구현
treeDataProvider.fillJsonData(data, {rows: "rows", icon: "icon"});
treeView.expandAll();
```

두 함수의 실행 결과는 동일 합니다.

#### 트리 구현을 위한 JSON 데이터의 계층 구조

트리를 구현하기 위한 JSON 데이터의 구조에 대해 조금 더 알아보겠습니다.

이 데모의 JSON 데이터 구조에서 주목할 부분은 `rows`라는 이름의 배열 속성 입니다.
이 속성은 트리의 계층구조를 표현하기 위한 속성명 입니다.
`rows` 속성은 자식 노드를 위한 속성입니다.
즉, JSON 에서 계층 구조는 계층을 표현하기 위한 속성(여기서는 `rows`)에 하위 노드의 데이터를 배열로 넣어주면 됩니다.

이 속성명은 JSON데이터로 트리를 구현하기 위한 `함수의 인자` 또는 `옵션의 속성`으로 넘겨주게 됩니다.

아래는 [TreeDataProvider.setJsonRows()](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)함수의 정의 입니다.
위 속성명인 `'rows'`는 이 함수의 두 번째 인자인 `rowsProp`의 값으로 넘겨 주어야 합니다.

```js
function setJsonRows(json, rowsProp, childrenProp, iconProp) {}
```

다음은 [TreeDataProvider.fillJsonData()](http://help.realgrid.com/api/TreeDataProvider/fillJsonData/)함수의 정의 입니다.
두 번째 인자인 `options` 즉 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)의
`rows`속성의 값으로 위 속성명인 `'rows'`를 넘겨 주어야 합니다.

```js
function fillJsonData(data, options) {}
```

일반적으로 SQL을 통해 데이터를 쿼리하는 방식으로 계층 데이터를 만들어내는 것은 쉽지 않습니다. 하지만,
JSON 데이터가 가지는 계층 구조를 직접 트리뷰 구현에 사용할 수 있기 때문에 <mark>NoSQL,
Document방식의 데이터를 트리뷰에 표현하기 위해 이 보다 좋은 방법은 없습니다.</mark>

RealGrid 튜토리얼에 계층 구조 표현을 위한 데이터 구조에 대해 좀더 자세히 다루고 있는 문서들이 있습니다. 아래 링크를 참조하세요.

  - [B9-1 배열형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-1/)
  - [B9-2 JSON형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-2/)
  - [B9-3 TreeView의 ItemModel 이해하기](http://help.realgrid.com/tutorial/b9-3/)

{% include_relative devbox/TreeIcon.md %}

{% comment %} ----------------- DEVBOX SCRIPT --------------- {% endcomment %}
<script>
  var data = {
    "rows":[
      { "icon":0, "do":"경기도",
        "rows":[
          { "icon":0, "do":"경기도", "si":"성남시",
            "rows":[
              { "icon":0, "do":"경기도", "si":"성남시", "gu":"분당구" },
              { "icon":0, "do":"경기도", "si":"성남시", "gu":"수정구" }
            ]
          },
          { "icon":0, "do":"경기도", "si":"수원시",
            "rows":[
              { "icon":0, "do":"경기도", "si":"수원시", "gu":"팔달구" },
              { "icon":0, "do":"경기도", "si":"수원시", "gu":"영통구" }
            ]
          },
          { "icon":0, "do":"경기도", "si":"안양시" },
          { "icon":0, "do":"경기도", "si":"의정부시" },
          { "icon":0, "do":"경기도", "si":"김포시" }
        ]
      }
    ]
  }

  $('#setJsonRows').click(function() {
    treeDataProvider.setJsonRows(data, "rows", "", "icon");
    treeView.expandAll();
  });

  $('#fillJsonData').click(function() {
    treeDataProvider.fillJsonData(data, {rows:"rows", icon:"icon"});
    treeView.expandAll();
  });

  $('.clearRows').click(function() {
    treeDataProvider.clearRows();
  });
</script>
