#### 셀 병합하기(Cell Merging)

`mergeRule.criteria`속성에 이전 행의 셀과 병합할 수식을 설정합니다.  
컬럼 설정 정보를 확인해 보세요.

```js
var columns = [{
    ...
    mergeRule: {
        criteria: "value"
    }
    ...
}]
```

#### 행들을 묶어서 표시하기

`mergeRule.criteria`속성에 설정한 조건에 따라 병합되는지 확인해보세요.

<a class="btn primary small round lowercase" id="row3">3행씩 병합</a>

```js
gridView.setColumnProperty("Country", "mergeRule", {criteria:"row div 3"})
```

<a class="btn primary small round lowercase" id="row5">5행씩 병합</a>

```js
gridView.setColumnProperty("Country", "mergeRule", {criteria:"row div 5"})
```

<a class="btn primary small round lowercase" id="value">동일 행 병합</a>

```js
gridView.setColumnProperty("Country", "mergeRule", {criteria:"value"})
```

<script>
$('#row3').click(function() {
  gridView.setColumnProperty("Country", "mergeRule", {criteria:"row div 3"})
});

$('#row5').click(function() {
  gridView.setColumnProperty("Country", "mergeRule", {criteria:"row div 5"})
});

$('#value').click(function() {
  gridView.setColumnProperty("Country", "mergeRule", {criteria:"value"})
});
</script>