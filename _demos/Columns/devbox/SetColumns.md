그리드 컬럼은 그리드에 연결된 데이터셋 한 필드의 값들을 표시하고 관리하는 View 모델입니다.
아래 버튼을 클릭하면 Javascript GridView.setColumns() 메쏘드를 호출하여 직접 그리드에 컬럼들을 추가합니다.

<a class="btn primary small round lowercase">컬럼 추가</a>

```js
var columns = [];

var column = new RealGrids.DataColumn();
column.name = "column1";
column.fieldName = "Field1";
column.header = { text: "Column 1" }
column.width = 150;
columns.push(column);
...
```

grid.setColumns(columns);
flash 그리드로 컬럼 정보를 전달할 때, 굳이 RealGrids.DataColumn 객체로 생성하여 전달할 필요는 없습니다. 아래 처럼 컬럼 정보들을 생성할 수도 있습니다. RealGrids.DataColumn 등 realgridplus.js에서 정의된 대부분의 클래스들은 명세로 존재합니다.


```js
var columns = [
// column1
{
    name : "column1",
    fieldName : "Field1",
    header : {
        text : "컬럼 1"
    },
    footer : {
    },
    styles : {
    },
    width : 150
},
// column 2
{
},
...
];
```

grid.setColumns(columns);
GridView.setColumns() 메쏘드는 매개변수로 전달되는 컬럼 정보 배열을 flash 그리드로 전달하여 기존 컬럼들을 지우고 새로운 컬럼들을 추가하도록 합니다. 예제에서 "column3"와 "column6"는 같은 값을 표시하고 있는데, 두 컬럼이 "Field3" 필드를 표시하고 있기 때문입니다. 즉, 하나의 데이터 필드를 여러 컬럼이 동시에 참조할 수 있으며, 같은 값을 각각 다른 방식으로 표시하는 요구 사항은 드물지 않습니다.
컬럼 name은 undefined이거나 그리드 내에서 유일해야 합니다. GridView.columnByName 메쏘드는 이 이름에 해당하는 javascript 컬럼 객체를 반환합니다. 컬럼의 tag 속성 값은 다양한 용도로 사용할 수 있는 사용자 지정 값입니다. 이 값은 중복될 수 있습니다. GridView.findColumnsByTag 메쏘드는 매개변수로 지정한 tag 값을 갖는 모든 컬럼들을 배열로 리턴 합니다. 이런 함수들이 리턴하는 컬럼들은 setColumns() 에서 전달한 컬럼 개체들입니다. 즉, javascript 내에서 생성되고 GridView에서 보관하는 컬럼 정보들인데, flash grid 내부에서 생성되는 컬럼 객체와는 양쪽에서 관리하는 id 값으로 연결되지만 속성들이 자동으로 동기화 되지는 않습니다.
컬럼은 각각 Header와 Footer를 표시하기 위한 정보를 갖습니다. 또한, 컬럼별로 스타일을 설정할 수 있습니다.
