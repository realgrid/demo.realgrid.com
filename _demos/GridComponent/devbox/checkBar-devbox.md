#### 체크바를 설정하는 방법
체크바의 설정을 변경하는 것은 [setCheckBar()](http://help.realgrid.com/api/GridBase/setCheckBar/)를 사용 합니다.  
현재 설정된 상태를 확인하는 것은 [getCheckBar()](http://help.realgrid.com/api/GridBase/getCheckBar/)을 사용 합니다.

#### 체크바의 화면 표시여부를 지정   
- `visible`: 체크바 영역의 화면 표시여부를 지정합니다. 

<a class="btn primary small round lowercase" id="btnSetVisibleFalse">표시하지 않음</a>

```js
gridView.setCheckBar({
  visible: false  
});
```

<a class="btn primary small round lowercase" id="btnSetVisibleTrue">표시</a>

```js
gridView.setCheckBar({
  visible: true  
});
```

#### 한 행만 체크 가능(라디오 버튼) 
체크바의 속성중 exclusive 속성을 true 로 설정하면 라디오 버튼처럼 하나의 행만 체크할 수 있습니다.

- `exclusive`: 하나의 행만 체크가능한지 여부를 지정합니다.  

<a class="btn primary small round lowercase" id="btnSetExclusiveTrue">하나의 행만 체크 가능</a>

```js
gridView.setCheckBar({
  exclusive: true  
});
```

<a class="btn primary small round lowercase" id="btnSetExclusiveFalse">모든 행 체크 가능</a>

```js
gridView.setCheckBar({
  exclusive: false  
});
```

#### 모두 체크
기본값으로 체크바의 헤드영역에 v 표시가 되어 있습니다. 이 영역을 클릭하게 되면 모든 행이 체크되게 됩니다.  

- `showAll`: 체크바 헤드 영역의 v 표시여부를 지정합니다. false 인 경우 헤드 영역을 클릭해도 모든 행이 체크되지 않습니다.  

<a class="btn primary small round lowercase" id="btnSetShowAllFalse">표시하지 않음</a>

```js
gridView.setCheckBar({
  showAll: false  
});
```

<a class="btn primary small round lowercase" id="btnSetShowAllTrue">표시</a>

```js
gridView.setCheckBar({
  showAll: true  
});
```

#### 체크하기
`한 행씩 체크할 수 있는 API`: [checkItem()](http://help.realgrid.com/api/GridBase/checkItem/), [checkRow()](http://help.realgrid.com/api/GridBase/checkRow/)  
`여러 행을 체크할 수 있는 API`: [checkItems()](http://help.realgrid.com/api/GridBase/checkItems/), [checkRows()](http://help.realgrid.com/api/GridBase/checkRows/)  
`전체 행을 체크할 수 있는 API`: [checkAll()](http://help.realgrid.com/api/GridBase/checkAll/)  

<a class="btn primary small round lowercase" id="btnCheckItemTrue">checkItem: 0행 체크</a>

```js
gridView.checkItem(0, true);  
```

<a class="btn primary small round lowercase" id="btnCheckItemFalse">checkItem: 0행 체크 해제</a>

```js
gridView.checkItem(0, false);  
```

아무 컬럼이나 컬럼의 헤더를 클릭하여 소트 후 아래 버튼을 클릭하세요.  
<a class="btn primary small round lowercase" id="btnCheckRowTrue">checkRow: 0행 체크</a>

```js
gridView.checkRow(0, true);  
```

<a class="btn primary small round lowercase" id="btnCheckRowFalse">checkRow: 0행 체크 해제</a>

```js
gridView.checkRow(0, false);  
```
dataRow, itemIndex가 다르기 때문에 결과가 다릅니다.   

<a class="btn primary small round lowercase" id="btnCheckItemsTrue">checkItems: [1, 2]행 체크</a>

```js
gridView.checkItems([1,2], true);  
```

<a class="btn primary small round lowercase" id="btnCheckItemsFalse">checkItems: [1, 2]행 체크 해제</a>

```js
gridView.checkItems([1,2], false);  
```

아무 컬럼의 헤더를 클릭하여 소트 후 아래 버튼을 클릭하세요.  
<a class="btn primary small round lowercase" id="btnCheckRowsTrue">checkRows: [1, 2]행 체크</a>

```js
gridView.checkRows([1,2], true);  
```

<a class="btn primary small round lowercase" id="btnCheckRowsFalse">checkRows: [1, 2]행 체크 해제</a>

```js
gridView.checkRows([1,2], false);  
```

#### Head/Foot
체크바의 헤드와 풋 영역에 글자나 이미지를 표시할 수 있습니다.  
아래 속성을 사용하려면 showAll속성의 값은 false 이어야 합니다.

- `headText`: head 영역에 표시할 text를 지정한다.    
- `footText`: foot 영역에 표시할 text를 지정한다.   
- `headImageUrl`: head 영역에 표시할 이미지의 Url을 지정한다.  
- `footImageUrl`: foot 영역에 표시할 이미지의 Url을 지정한다.  

<a class="btn primary small round lowercase" id="btnSetText">Text 표시</a>

```js
gridView.setCheckBar({
  showAll: false,
  headText: "H",  
  footText: "F",
  headImageUrl: null,  
  footImageUrl: null  
});
```

<a class="btn primary small round lowercase" id="btnSetImage">Image 표시</a>

```js
gridView.setCheckBar({
  showAll: false,
  headText: null,  
  footText: null,
  headImageUrl: "/resource/image/common/dot_arrow2_top.gif",  
  footImageUrl: "/resource/image/common/dot_arrow2_bottom.gif"  
});
```

#### Checkable 제어
아래와 같은 수식을 사용하여 체크바에 체크 가능 여부를 제어할 수 있습니다. [expression 참고](http://demo.realgrid.com/Demo/ExpressionConcept)  
`state = 'c'`: 새로 추가된 행만 체크 가능   
`values['OrderID'] = '10248'`: OrderID필드값이 10248인 행만 체크 가능   
`row < 10`: itemIndex가 10 이하인 행만 체크 가능    
`datarow < 10`: dataRow가 10 이하인 행만 체크 가능  

이러한 수식들을 checkBar.checkableExpression 에 설정 후 [gridView.applyCheckable()](http://help.realgrid.com/api/GridBase/applyCheckables/) 사용하여 그리드에 적용시킬 수 있습니다.  
[gridView.setCheckableExpression()](http://help.realgrid.com/api/GridBase/setCheckableExpression/)을 사용하여 설정과 적용을 한번에 적용할 수도 있습니다.  
적용된 체커블 상태의 초기화는 [gridView.resetCheckables()](http://help.realgrid.com/api/GridBase/resetCheckables/)을 사용합니다.  

<a class="btn primary small round lowercase" id="btnCheckableExpression">수식만 설정</a>

```js
gridView.setCheckBar({
  checkableExpression: "values['OrderID'] = '10248'"
});
```

<a class="btn primary small round lowercase" id="btnApplyCheckables">수식을 그리드에 적용</a>

```js
gridView.applyCheckables();
```

<a class="btn primary small round lowercase" id="btnSetCheckableExpression">수식의 설정과 적용을 동시에</a>

```js
gridView.setCheckableExpression("row < 10", true);
```

<a class="btn primary small round lowercase" id="btnResetCheckables">초기화</a>

```js
gridView.resetCheckables();
```


<script>

  $('#btnSetVisibleFalse').click(function() {
    gridView.setCheckBar({
      visible: false  
    });
  });

  $('#btnSetVisibleTrue').click(function() {
    gridView.setCheckBar({
      visible: true  
    });
  });

  $('#btnSetExclusiveTrue').click(function() {
    gridView.setCheckBar({
      exclusive: true  
    });
  });

  $('#btnSetExclusiveFalse').click(function() {
    gridView.setCheckBar({
      exclusive: false  
    });
  });

   $('#btnSetShowAllFalse').click(function() {
    gridView.setCheckBar({
      showAll: false  
    });
  });

  $('#btnSetShowAllTrue').click(function() {
    gridView.setCheckBar({
      showAll: true     
    });
  }); 

  $('#btnCheckItemTrue').click(function() {
    gridView.checkItem(0, true); 
  }); 

  $('#btnCheckItemFalse').click(function() {
    gridView.checkItem(0, false); 
  }); 

  $('#btnCheckRowTrue').click(function() {
    gridView.checkRow(0, true); 
  }); 

  $('#btnCheckRowFalse').click(function() {
    gridView.checkRow(0, false); 
  }); 

  $('#btnCheckItemsTrue').click(function() {
    gridView.checkItems([1,2], true); 
  }); 

  $('#btnCheckItemsFalse').click(function() {
    gridView.checkItems([1,2], false); 
  }); 

  $('#btnCheckRowsTrue').click(function() {
    gridView.checkRows([1,2], true); 
  }); 

  $('#btnCheckRowsFalse').click(function() {
    gridView.checkRows([1,2], false); 
  });   

  $('#btnSetText').click(function() {
    gridView.setCheckBar({
      showAll: false,
      headText: "H",  
      footText: "F",
      headImageUrl: null,  
      footImageUrl: null  
    });
  });

  $('#btnSetImage').click(function() {
    gridView.setCheckBar({
      showAll: false,
      headText: null,  
      footText: null,
      headImageUrl: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/dot_arrow2_top.gif",  
      footImageUrl: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/dot_arrow2_bottom.gif"  
    });
  });  

  $('#btnCheckableExpression').click(function() {
    gridView.setCheckBar({
      checkableExpression: "values['OrderID'] = '10248'"
    }); 
  });   

  $('#btnApplyCheckables').click(function() {
    gridView.applyCheckables();
  });   

  $('#btnSetCheckableExpression').click(function() {
    gridView.setCheckableExpression("row < 10", true);
  });   

  $('#btnResetCheckables').click(function() {
    gridView.resetCheckables(); 
  });   

</script>
