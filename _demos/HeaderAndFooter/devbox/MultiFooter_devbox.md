#### 멀티 푸터

- `footer.count`: 지정한 수 만큼 그리드 하단에 footer를 표시합니다.
- `footer.height`: footer의 전체 높이를 지정합니다.

count에 지정한 수 만큼 footer의 높이가 자동으로 조절되지는 않습니다. 직접 높이를 지정해야 합니다.  

```js
gridView.setFooter({
  "count" : 2,
  "height" : 50
});
```

푸터에 표시할 수식과 문자열은 Column.Footer.Expression, Column.Footer.Text를 배열로 지정로 지정합니다. 

```js
var columns = [{
...
    "name": "QuantityPerUnit",
    "fieldName": "QuantityPerUnit",
    "type": "data",
    "width": "140",
    "styles": {
        "textAlignment": "near"
    },
    "header": {
        "text": "Quantity / Unit"
    },
    "footer": {
        "styles": {
            "textAlignment": "far",
            "font": "굴림,12"
        },
        "text": ["합계 =>", "평균 =>"],    //<<-- 문자열
        "groupText": "합계 =>"
    }
}, {
    "name": "Quantity",
    "fieldName": "Quantity",
    "type": "data",
    "width": "100",
    "styles": {
        "textAlignment": "far"
    },
    "header": {
        "text": "Quantity"
    },
    "footer": {
        "styles": { 
            "textAlignment": "far",
            "numberFormat": "#,##0",
            "suffix": " $", 
            "font": "Arial,12"
            },
        "expression": ["sum", "avg"],   //<<-- 수식  
        "groupExpression": "sum"
    }
}, {
...
}];
```

<a class="btn primary small round lowercase" id="btnSetFooter">3행 푸터 지정</a>

```js
gridView.setFooter({
  "count" : 3,
  "height" : 75
});
```

<a class="btn primary small round lowercase" id="btnSetColumnFooter">Quantity컬럼 Footer3행에 표준편차 표시</a>

```js
var footer = gridView.getColumnProperty("QuantityPerUnit", "footer");
footer.text = ["합계 =>", "평균 =>", "표준편차 =>"];

gridView.setColumnProperty("QuantityPerUnit", "footer", footer);  

footer = gridView.getColumnProperty("Quantity", "footer");
footer.expression = ["sum", "avg", "stdev"];

gridView.setColumnProperty("Quantity", "footer", footer);  
```

<script>

  $('#btnSetFooter').click(function() {
    gridView.setFooter({
      "count" : 3,
      "height" : 75
    });
  });

  $('#btnSetColumnFooter').click(function() {
    var footer = gridView.getColumnProperty("QuantityPerUnit", "footer");
    footer.text = ["합계 =>", "평균 =>", "표준편차 =>"];

    gridView.setColumnProperty("QuantityPerUnit", "footer", footer);  

    footer = gridView.getColumnProperty("Quantity", "footer");
    footer.expression = ["sum", "avg", "stdev"];

    gridView.setColumnProperty("Quantity", "footer", footer);      
  });


</script>
