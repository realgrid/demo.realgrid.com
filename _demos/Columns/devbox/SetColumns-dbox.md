그리드 컬럼은 그리드에 연결된 데이터셋 한 필드의 값들을 표시하고 관리하는 View 모델입니다.
아래 버튼을 클릭하면 GridBase.setColumns() 함수를 호출하여 직접 그리드에 컬럼들을 추가합니다.

<a class="btn primary small round lowercase" id="btnColumns">컬럼 추가</a>

```js
var columns = [];

var column = new RealGridJS.DataColumn();
column.name = "column1";
column.fieldName = "Field1";
column.header = { text: "Column 1" }
column.tag = "columntag1";
column.width = 110;
columns.push(column);

column = new RealGridJS.DataColumn();
column.name = "column2";
column.fieldName = "Field2";
column.tag = "columntag1";
column.header = { text: "Column 2" }
column.width = 110;
columns.push(column);

column = new RealGridJS.DataColumn();
column.name = "column3";
column.fieldName = "Field3";
column.header = { text: "Column 3" }
column.width = 110;
column.styles = { background: "#33ffff00" };
columns.push(column);

column = new RealGridJS.DataColumn();
column.name = "column4";
column.fieldName = "Field4";
column.header = { text: "Column 4" }
column.width = 110;
columns.push(column);

column = new RealGridJS.DataColumn();
column.name = "column5";
column.fieldName = "Field5";
column.header = { text: "Column 5" }
column.width = 110;
columns.push(column);

column = new RealGridJS.DataColumn();
column.name = "column6";
column.fieldName = "Field3";
column.header = { text: "Column 6" }
column.width = 110;
column.styles = { background: "#33ffff00" };
columns.push(column);

gridView.setColumns(columns);
```


그리드로 컬럼 정보를 전달할 때, RealGridJS.DataColumn 객체로 생성하지않고 아래 처럼 컬럼 정보들을 생성할 수도 있습니다. RealGridJS.DataColumn 등의 Class들은 realgridjs-api에 명세로 존재합니다.


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
grid.setColumns(columns);
```

GridBase.setColumns() 함수는 매개변수로 전달되는 컬럼 정보 배열을 그리드로 전달하여 기존 컬럼들을 지우고 새로운 컬럼들을 추가하도록 합니다. 
예제에서 "column3"와 "column6"는 같은 값을 표시하고 있는데, 두 컬럼이 "Field3" 필드를 표시하고 있기 때문입니다. 즉, 하나의 데이터 필드를 여러 컬럼이 동시에 참조할 수 있으며, 같은 값을 각각 다른 방식으로 표시하는 요구 사항은 드물지 않습니다.
컬럼 name은 undefined이거나 그리드 내에서 유일해야 합니다. 

GridBase.columnByName() 함수는 주어진 이름에 해당하는 컬럼 객체를 반환합니다. 아래의 버튼을 클릭하면 name이 "column3"인 컬럼을 찾아 object 문자열 형태로 출력합니다.

<a class="btn primary small round lowercase" id="btnColumnByName">columnByName</a>
```js
var column = gridView.columnByName("column3");
alert(JSON.stringify(column));
```
GridBase.columnsByField() 함수는 Field이름에 해당하는 컬럼 객체들을 배열로 반환합니다. 결과가 하나로 예상 되는경우는 columnByField()함수를 사용합니다.
아래의 버튼을 클릭하면 fieldName이 "Field3"인 컬럼을 찾아 그 갯수를 출력합니다. 

<a class="btn primary small round lowercase" id="btnColumnsByField">columnsByField</a>
```js
var columns = gridView.columnsByField("Field3");
alert(columns.length);
```

컬럼의 tag 속성 값은 다양한 용도로 사용할 수 있는 사용자 지정 값입니다. 이 값은 중복될 수 있습니다. GridBase.columnsByTag() 함수는 매개변수로 지정한 tag 값을 갖는 모든 컬럼들을 배열로 리턴 합니다. 
결과가 하나로 예상 되는경우는 columnByTag()함수를 사용합니다.
아래의 버튼을 클릭하면 tag가 "columntag1"인 컬럼을 찾아 그 갯수를 출력합니다. 

<a class="btn primary small round lowercase" id="btnColumnsByTag">columnsByTag</a>
```js
var columns = gridView.columnsByTag("columntag1");
alert(columns.length);
```

이런 함수들이 리턴하는 컬럼들은 setColumns() 에서 전달한 컬럼 개체들입니다. 즉, javascript 내에서 생성되고 Grid에서 보관하는 컬럼 정보들인데, grid 내부에서 생성되는 컬럼 객체와는 양쪽에서 관리하는 id 값으로 연결되지만 속성들이 자동으로 동기화 되지는 않습니다.
컬럼은 각각 Header와 Footer를 표시하기 위한 정보를 갖습니다. 또한, 컬럼별로 스타일을 설정할 수 있습니다.

<script>

$('#btnColumns').click(function() {
    var flds = dataProvider.getFieldCount();
    if (flds > 0) {
        var rows = [];

        for (var i = 0; i < 10; i++) {
            var row = [];
            for (var c = 0; c < flds; c++) {
                row.push("Cell(" + i + ", " + c + ")");
            }
            rows.push(row);
        }

        dataProvider.setRows(rows);
    }

    var columns = [];

    var column = new RealGridJS.DataColumn();
    column.name = "column1";
    column.fieldName = "Field1";
    column.header = { text: "Column 1" }
    column.tag = "columntag1";
    column.width = 110;
    columns.push(column);

    column = new RealGridJS.DataColumn();
    column.name = "column2";
    column.fieldName = "Field2";
    column.tag = "columntag1";
    column.header = { text: "Column 2" }
    column.width = 110;
    columns.push(column);

    column = new RealGridJS.DataColumn();
    column.name = "column3";
    column.fieldName = "Field3";
    column.header = { text: "Column 3" }
    column.width = 110;
    column.styles = { background: "#33ffff00" };
    columns.push(column);

    column = new RealGridJS.DataColumn();
    column.name = "column4";
    column.fieldName = "Field4";
    column.header = { text: "Column 4" }
    column.width = 110;
    columns.push(column);

    column = new RealGridJS.DataColumn();
    column.name = "column5";
    column.fieldName = "Field5";
    column.header = { text: "Column 5" }
    column.width = 110;
    columns.push(column);

    column = new RealGridJS.DataColumn();
    column.name = "column6";
    column.fieldName = "Field3";
    column.header = { text: "Column 6" }
    column.width = 110;
    column.styles = { background: "#33ffff00" };
    columns.push(column);

    gridView.setColumns(columns);
});
$('#btnColumnByName').click(function() {
    var column = gridView.columnByName("column3");
    alert(JSON.stringify(column));
});
$('#btnColumnsByField').click(function() {
    var columns = gridView.columnsByField("Field3");
    alert(columns.length);
});
$('#btnColumnsByTag').click(function() {
    var columns = gridView.columnsByTag("columntag1");
    alert(columns.length);
});
</script>