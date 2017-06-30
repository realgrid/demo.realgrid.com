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

*멀티 푸터 스타일 설정*

버튼 클릭 시 "Quantity" 컬럼의 footer행 별로 스타일을 설정할 수 있습니다.

<a class="btn primary small round lowercase" id="btnSetMultiFooterStyles">동적 컬럼 푸터 스타일</a>

```js
gridView.setColumnProperty("Quantity","footer", {
    styles:[{
        background:"#ffffff00",
        textAlignment:"far",
        numberFormat:"#,##0.#"
    },{
        background:"#ff00ffff",
        textAlignment:"far",
        numberFormat:"#,##0.##"
    },{
        background:"#ff11ff55",
        textAlignment:"far",
        numberFormat:"#,##0.###"
    }]
});
```

모든 푸터 행에 스타일을 설정할 수 있습니다.

<a class="btn primary small round lowercase" id="btnSetMultiFooterStyleRows">전체 푸터 행 스타일</a>

```js
gridView.setFooter({styles:[{
        background:"#ffffff00"
    },{
        background:"#ff00ffff"
    },{
        background:"#ff11ff55"
    }]
})
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

  $('#btnSetMultiFooterStyles').click(function() {
    gridView.setColumnProperty("Quantity","footer", {
        styles:[{
            background:"#ffffff00",
            textAlignment:"far",
            numberFormat:"#,##0.#"
        },{
            background:"#ff00ffff",
            textAlignment:"far",
            numberFormat:"#,##0.##"
        },{
            background:"#ff11ff55",
            textAlignment:"far",
            numberFormat:"#,##0.###"
        }]
    });
  });

  $('#btnSetMultiFooterStyleRows').click(function() {
    gridView.setFooter({styles:[{
            background:"#ffffff00"
        },{
            background:"#ff00ffff"
        },{
            background:"#ff11ff55"
        }]
    })
  });


</script>
