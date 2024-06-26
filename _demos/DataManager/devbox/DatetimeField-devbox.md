#### 날짜 데이터

아래는 예제에 사용된 각 컬럼별 datetimeFormat에 해당 하는 데이터 형태입니다.

```js
var data = [
    ["20141114", "20141114PM051215008", "20141114171215008", "2014/11/14 17:12", "2014-11-14T17:12:15+09:00"],
    ["20141115", "20140304AM040805556", "20140304040805556", "2014/03/04 04:08", "2014-03-04T04:08:05+09:00"],
    ["20010215", "20010215PM124236721", "20010215124236721", "2001/02/15 12:42", "2001-02-15T12:42:36+09:00"],
    ["20111025", "20111025AM103637426", "20111025103637426", "2011/10/25 10:36", "2011-10-25T10:36:37+09:00"],
    ["20070626", "20070626PM030456962", "20070626150456962", "2007/06/26 15:04", "2007-06-26T15:04:56+09:00"],
    ["20040807", "20040807AM013302430", "20040807013302430", "2004/08/07 01:33", "2004-08-07T01:33:02+09:00"],
    ["20050530", "20050530AM105829932", "20050530105829932", "2005/05/30 10:58", "2005-05-30T10:58:29+09:00"],
    ["20071030", "20071030AM083042626", "20071030083042626", "2007/10/30 08:30", "2007-10-30T08:30:42+09:00"],
    ["20030629", "20030629PM063304071", "20030629183304071", "2003/06/29 18:33", "2003-06-29T18:33:04+09:00"],
    ["20130807", "20130807PM082825025", "20130807202825025", "2013/08/07 20:28", "2013-08-07T20:28:25+09:00"]
];

dataProvider.setRows(data);
```

#### datetimeFormat 설정

[loadData()](http://help.realgrid.com/api/DataProvider/loadData/)를 통해 Datetime 형의 값이 문자열로 전달되거나, [setRows()](http://help.realgrid.com/api/LocalDataProvider/setRows/) 함수 등으로 javascript에서 문자열로 Date 필드의 값을 전달할 때, 그 문자열은 아래와 같이 리얼그리드가 Datetime 형의 값으로 인식할 수 있는 형태를 설정해야 합니다.

```js
dataProvider.setFields([{
        fieldName: "Datetime1",
        dataType: "datetime",
        datetimeFormat: "yyyyMMdd"
    }, {
    ...
}]);
```

사용자의 입력을 Datetime 값으로 변환하고, Datetime 값을 에디터에 표시하기 위한 형식을 `editor`의 datetimeFormat속성을 아래와 같은 형식으로 지정합니다.

```js 
gridView.setColumns([{
    name: "Datetime1",
    fieldName: "Datetime1",
    width: "110",
    header: "YYYYMMDD",
    editor: {
        datetimeFormat: "yyyy-MM-dd"
    }
    ...
}]);
```

Datetime 필드의 값을 표시하는 셀 렌더러는 datetimeFormat `스타일` 값을 사용합니다.

```js 
gridView.setColumns([{
    name: "Datetime1",
    fieldName: "Datetime1",
    width: "110",
    header: "YYYYMMDD",
    styles: {
        datetimeFormat: "yyyy/MM/dd"
    }
    ...
}]);
```