#### Lookup Tree 설정

[setLookups](http://help.realgrid.com/api/GridBase/setLookups/) 함수를 사용해서 lookup tree에서 사용할 lookup source들을 등록합니다.  
등록된 lookup source의 id인 `customers`를 컬럼의 lookupSourceId속성에 설정하고 lookupKeyFields에 참조 키값으로 사용될 필드의 목록을 설정해야 합니다.

```js
//lookup tree에서 사용할 lookup source들을 등록
gridView.setLookups([{
    id: "customers",
    levels: 2,
    keys: [
        ["France", "VINET"],
        ["France", "VICTE"],
        ["Germany", "TOMSP"],
        ["Brazil", "HANAR"]
    ],
    values: [
        "Vins et alcools Chevalier",
        "Victuailles en stock",
        "Toms Spezialitäten",
        "Hanari Carnes"
    ]
}]);

//컬럼생성시 lookupSourceId와 lookupKeyFields를 설정합니다.
gridView.setColumns([
    ...
    {
        name: "CustomerID2",
        fieldName: "CustomerID",
        type: "data",
        width: "200",
        lookupDisplay: "true",
        lookupSourceId: "customers",
        lookupKeyFields: [
            "Country",
            "CustomerID"
        ],
        styles: {
            background: "#ffffff99",
            textAlignment: "center"
        },
        header: {
            text: "Customer ID 3"
        }
    }
    ...
]);
```

#### 동적 dropDown리스트

dropDown리스트가 동적으로 앞의 값에 따라 변경되도록 설정하는 방법입니다.

```js
//사용자 입력이 셀에 반영될때 발생하는 이벤트
gridView.onEditCommit = function (id, index, oldValue, newValue) {
    if (index.field == "Country") {
        lookupDataChange(newValue);
    }
};

//그리드의 포커스 셀의 위치가 변경된 후 발생하는 이벤트
gridView.onCurrentChanged = function (grid, newIndex) {
    if (newIndex && newIndex.dataRow > -1) {
        var keyValue = grid.getValue(newIndex.itemIndex, "Country");
        lookupDataChange(keyValue);
    }
};

//해당 이벤트의 keyValue값에 해당하는 lookupSource에 lookupData를 추가
function lookupDataChange(keyValue) {
    if (oldKey != keyValue) {
        var params = { country: keyValue };
 
        $.getJSON("/Demo/GetCustomerByCountry", params, function (data) {
            var lookups = [];
            for (var i in data) {
                if (!gridView.existsLookupData("customers", [data[i].Country, data[i].CustomerID])) {
                    var lookup = [data[i].Country, data[i].CustomerID, data[i].CompanyName];
                    lookups.push(lookup);
                }
            }
            gridView.fillLookupData("customers", {
                rows: lookups
            });
        });
 
        oldKey = keyValue;
    }
}
```