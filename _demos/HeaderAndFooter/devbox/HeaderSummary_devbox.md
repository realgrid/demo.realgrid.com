#### 헤더 합계

- `header.summary.visible`: 속성값을 true로 설정하면 footer와 같은 기능을 가진 bar를 시작 위치에 표시 합니다.

```js
gridView.setHeader({
    summary: {
        visible: true,
        styles: {
            background: "#11ff0000"
        }
    }
})
...
gridView.setColumns([{
    ...
}, {
    "fieldName": "Quantity",
    },
    "header": {
        "text": "Quantity",
        "summary": {
            "styles": {
                "textAlignment": "far",
                "numberFormat": "#,##0",
                "suffix": " $",
                "font": "Arial,12"
            },
            "text": "합계",
            "expression": "sum"
        }
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
