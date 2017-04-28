#### 컬럼의 일렬배치
[linearizeColumns()](http://help.realgrid.com/api/GridBase/linearizeColumns/%20-%20layout){:target="_blank"} 함수를 호출해서 컬럼 그룹들을 모두 제거하고 데이터 값을 표시하는 컬럼들만 일렬로 배치합니다.

<a class="btn primary small round lowercase" id="btnLinearizeColumn">Linearize</a>

```js
gridView.restoreColumns();
gridView.linearizeColumns();
gridView.setFocus();
```

다시 원래대로 복원할 수도 있습니다.

<a class="btn primary small round lowercase" id="btnRestore">Restore</a>

```js
gridView.restoreColumns();
gridView.setFocus();
```

#### 컬럼 레이아웃 지정하기
[setColumnLayout()](http://help.realgrid.com/api/GridBase/setColumnLayout/){:target="_blank"} 함수를 통해 컬럼 layout을 최초 설정한 컬럼들의 이름들로 지정할 수 있습니다.

<a class="btn primary small round lowercase" id="btnSetColumnLayout">Set Column Layout</a>

```js
var layout = [
    "OrderID", "EmployeeID", "OrderDate", "CompanyName", "CustomerID"
];

gridView.setColumnLayout(layout);
gridView.setFocus();
```

#### 컬럼 레이아웃 등록, 사용하기
[registerColumnLayouts()](http://help.realgrid.com/api/GridBase/registerColumnLayouts/){:target="_blank"} 함수로 실행 시간에 지정할 컬럼 layout들을 미리 저장한 후, setColumnLayout() 함수로 layout 이름을 지정해서 변경할 수 있습니다.

layout1, layout2로 컬럼 레이아웃을 만들어 봅니다.  

<a class="btn primary small round lowercase" id="btnRegisterColumnLayouts">layout1, layout2 만들기</a>

```js
var layouts = [{
    name: "layout1",
    columns: [
        "OrderID", "EmployeeID", "OrderDate"
    ]
}, {
    name: "layout2",
    columns: [{
        "header": "Order",
        "orientation": "vertical",
        "width": 150,
        "columns": [
            {
                "header": "IDs",
                "orientation": "horizontal",
                "width": 200,
                "columns": [
                    "OrderID",
                    "EmployeeID"
                ]
            },
            "OrderDate"
        ]
    }]
}];

gridView.registerColumnLayouts(layouts);
```

[registerColumnLayouts()](http://help.realgrid.com/api/GridBase/registerColumnLayouts/){:target="_blank"}으로 설정한 컬럼 레이아웃으로 설정하기.

<a class="btn primary small round lowercase" id="btnLayout1">layout1 로 설정하기</a>

```js
gridView.restoreColumns();
gridView.setColumnLayout("layout1");
gridView.setFocus();
```

<a class="btn primary small round lowercase" id="btnLayout2">layout2 로 설정하기</a>

```js
gridView.restoreColumns();
gridView.setColumnLayout("layout2");
gridView.setFocus();
```

#### 현재 컬럼 레이아웃 저장하고 복원하기  
[saveColumnLayout](http://help.realgrid.com/api/GridBase/saveColumnLayout/){:target="_blank"} 함수로 현재 상태를 저장한 후, 저장된 값을 가져와서 setColumnLayout 함수로 layout을 변경할 수 있습니다.

<a class="btn primary small round lowercase" id="btnSaveColumnLayout">현재상태 저정하기</a>

```js
var dispCols = gridView.saveColumnLayout();
```
<a class="btn primary small round lowercase" id="btnLoadLayout">저장된 레이아웃으로 복원</a>

```js
gridView.setColumnLayout(dispCols);
```

<script>
var dispCols = [];

$("#btnLinearizeColumn").click(function() { 
  gridView.restoreColumns();
  gridView.linearizeColumns();
  gridView.setFocus();
});

$("#btnRestore").click(function() { 
  gridView.restoreColumns();
  gridView.setFocus();
});

$("#btnSetColumnLayout").click(function() { 
  var layout = [
      "OrderID", "EmployeeID", "OrderDate", "CompanyName", "CustomerID"
  ];

  gridView.setColumnLayout(layout);
  gridView.setFocus();
});

$("#btnRegisterColumnLayouts").click(function() { 
  var layouts = [{
      name: "layout1",
      columns: [
          "OrderID", "EmployeeID", "OrderDate"
      ]
  }, {
      name: "layout2",
      columns: [{
          "header": "Order",
          "orientation": "vertical",
          "width": 150,
          "columns": [
              {
                  "header": "IDs",
                  "orientation": "horizontal",
                  "width": 200,
                  "columns": [
                      "OrderID",
                      "EmployeeID"
                  ]
              },
              "OrderDate"
          ]
      }]
  }];

  gridView.registerColumnLayouts(layouts);
});

$("#btnLayout1").click(function() { 
  gridView.restoreColumns();
  gridView.setColumnLayout("layout1");
  gridView.setFocus();
});

$("#btnLayout2").click(function() { 
  gridView.restoreColumns();
  gridView.setColumnLayout("layout2");
  gridView.setFocus();
});

$("#btnSaveColumnLayout").click(function() { 
  dispCols = gridView.saveColumnLayout();
});

$("#btnLoadLayout").click(function() { 
  gridView.setColumnLayout(dispCols);
});



</script>

