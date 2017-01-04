#### CustomerID 컬럼

"Custom ID" 컬럼은 `font-bold` 를 true로 지정했습니다. 

``` js
styles: {
    textAlignment: "center",
    font: "Tahoma",
    fontBold: true
},
```

#### EmployeeID 컬럼

"Employee ID" 컬럼은 `foreground` 를 "#ffff0000"로 붉게 했습니다. 

```js
styles: {
    textAlignment: "center",
    font: "Arial",
    foreground: "#ffff0000"
},
```

#### UnitPrice 컬럼

"Unit Price" 컬럼은 숫자 컬럼인데 `textAlignment`를 "far"로, `suffix`를 "$"로 지정했습니다. 

```js
styles: {
    textAlignment: "far",
    paddingRight: 5,
    suffix: " $",
    font: "Arial,12,bold"
},
```

#### Quantity 컬럼

"Quantity" 컬럼 역시 숫자 컬럼인데 `numberFormat`를 "00.00"로 지정해서 소수점 두자리가 항상 표시되도록 했습니다. 

```js
styles: {
    textAlignment: "far",
    font: "Arial",
    paddingRight: 5,
    numberFormat: "00.00",
    foreground: "#0000ff"
},
```

#### OrderDate 컬럼

"Order Date"는 날짜형 컬럼인데 `datetimeFormat`을 "yyyy-MM-dd HH:mm"로 지정했습니다.

```js
 styles: {
    textAlignment: "center",
    font: "Tahoma",
    datetimeFormat: "yyyy-MM-dd"
},
```