#### 컬럼 푸터

- `footer.visible`: 그리드 하단에 footer를 표시합니다.

```js
// 컬럼 설정시 합계 식 지정
gridView.setColumns([{
    ...
}, {
    "fieldName": "QuantityPerUnit",
    "footer": {
        "text": "합계 =>"
    }
}, {
    "fieldName": "Quantity",
    },
    "footer": {
        "styles": {
            "textAlignment": "far",
            "numberFormat": "#,##0",
            "suffix": " $",
            "font": "Arial,12"
            },
        "text": "합계",
        "expression": "sum",
        "groupExpression": "sum"
    }
}, {
    ...
}];
```

footer와 같이 summary mode를 **"statistical"**로 지정해야 분산, 표준편차 값이 표시 됩니다.

<a class="btn primary small round lowercase" id="btnSetStatistical">Statistical 모드 적용</a>

```js
  gridView.setOptions({"summaryMode" : "statistical"});
```

<a class="btn primary small round lowercase" id="btnSetAggregate">Aggregate 모드 적용</a>

```js
  gridView.setOptions({"summaryMode" : "aggregate"});
```


<a class="btn primary small round lowercase" id="btnSetNone">None 모드 적용</a>  
컬럼의 합계를 계산하지 않습니다.

```js
  gridView.setOptions({"summaryMode" : "none"});
```


Help 사이트의 [summary Mode](http://help.realgrid.com/api/types/SummaryMode/){:target="_blank"} 참고 바랍니다.  

<script>

  $('#btnSetStatistical').click(function() {
    gridView.setOptions({"summaryMode" : "statistical"});
  });

  $('#btnSetAggregate').click(function() {
    gridView.setOptions({"summaryMode" : "aggregate"});
  });

  $('#btnSetNone').click(function() {
    gridView.setOptions({"summaryMode" : "none"});
  });

</script>
