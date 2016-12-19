#### calculateExpression 설정

자동으로 계산될 필드는 `calculateExpression`를 사용해서 `calculateField`로 설정할 수 있습니다.
Calculate Field와 연결된 컬럼은 readOnly가 됩니다.
`※ 자기 자신 필드를 calculateExpression에 사용할 수 없습니다.`

```js
var fields = [{
    fieldName: "Quantity",
    dataType: "number"
}, {
    fieldName: "UnitPrice",
    dataType: "number"
}, {
    fieldName: "Price",
    dataType: "number",
    calculateExpression: "values['Quantity'] * values['UnitPrice']"
}]
```

#### calculateCallback 설정

계산식으로 표현하기 어려운 경우 `calculateCallback`함수를 통해 값을 구할 수 있습니다.

```js
var fields = [{
    fieldName: "Quantity",
    dataType: "number"
}, {
    fieldName: "UnitPrice",
    dataType: "number"
}, {
	fieldName: "Price",
	dataType: "number",
	calculateCallback: function (dataRow, fieldName, fieldNames, values) {
	    var quantity = values[fieldNames.indexOf("Quantity")];
	    var unitprice = values[fieldNames.indexOf("UnitPrice")];
	    if (isNaN(quantity) || isNaN(unitprice))
	        return undefined;
	    else
	        return quantity >= 1000 ? Math.round(quantity * unitprice * 0.95) : quantity * unitprice;
	}
}]
```