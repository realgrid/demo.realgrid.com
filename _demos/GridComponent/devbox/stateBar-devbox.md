#### 상태바를 설정하는 방법
상태바의 설정을 변경하는 것은 [setStateBar()](http://help.realgrid.com/api/GridBase/setStateBar/)를 사용 합니다.   
현재 설정된 상태를 확인하는 것은 [getStateBar()](http://help.realgrid.com/api/GridBase/getStateBar/)을 사용 합니다.    
#### 상태바의 화면 표시여부를 지정   

- `visible`: 상태바 영역의 화면 표시여부를 지정합니다. 

<a class="btn primary small round lowercase" id="btnSetVisibleFalse">표시하지 않음</a>

```js
gridView.setStateBar({
  visible: false  
});
```

<a class="btn primary small round lowercase" id="btnSetVisibleTrue">표시</a>

```js
gridView.setStateBar({
  visible: true  
});
```

#### 행 상태 변경하기  
행 상태(RowState)는 사용자의 키 입력에 의해서 변경되지만 개발자가 임의로 설정할 수 있습니다.  
아래 버튼은 현재 선택된 행의 상태를 변경합니다. 

<div class="radio">
  <label>
    <input type="radio" name="rowState" value="created" checked="checked">created  <br />
    <input type="radio" name="rowState" value="updated">updated  <br /> 
    <input type="radio" name="rowState" value="deleted">deleted  <br /> 
    <input type="radio" name="rowState" value="createAndDeleted">createAndDeleted  <br /> 
    <input type="radio" name="rowState" value="none">none <br />  
  </label>
</div>

<a class="btn primary small round lowercase" id="btnSetRowState">행 상태 변경하기</a>


```js
var curr = gridView.getCurrent();
var rowState = $(":input:radio[name='rowState']:checked").val()
dataProvider.setRowState(curr.dataRow, rowState)
```


#### 표시형태 변경하기
기본적으로 각 행의 상태는 아이콘으로 표시 됩니다. 그라나 필요에 따라 text로 보여주기를 원할때도 있습니다.
이런 경우 stateBar.mark 속성에 text를 지정하고 stateTexts 속성에 각 상태별 문자를 지정하면 됩니다.   

<a class="btn primary small round lowercase" id="btnSetCheckBarText">Text로 표시</a>

```js
gridView.setStateBar({
    mark: "text",
    stateTexts: {
        created: "C",
        updated: "U",
        deleted: "D",
        createAndDeleted: "X"
    }
});    
```

<a class="btn primary small round lowercase" id="btnSetCheckBarDefault">Default로 표시(아이콘)</a>

```js
gridView.setStateBar({
    mark: "default"
}); 
```

<a class="btn primary small round lowercase" id="btnSetZeroBaseFalse">1부터 시작</a>

```js
gridView.setIndicator({
  zeroBase: false  
});
```

#### Head/Foot
상태 바의 헤드와 풋 영역에 글자나 이미지를 표시할 수 있습니다.

- `headText`: head 영역에 표시할 text를 지정한다.    
- `footText`: foot 영역에 표시할 text를 지정한다.   
- `headImageUrl`: head 영역에 표시할 이미지의 Url을 지정한다.  
- `footImageUrl`: foot 영역에 표시할 이미지의 Url을 지정한다.  

<a class="btn primary small round lowercase" id="btnSetText">Text 표시</a>

```js
gridView.setStateBar({
  headText: "H",  
  footText: "F",
  headImageUrl: null,  
  footImageUrl: null  
});
```

<a class="btn primary small round lowercase" id="btnSetImage">Image 표시</a>

```js
gridView.setStateBar({
  headText: null,  
  footText: null,
  headImageUrl: "/resource/image/common/dot_arrow2_top.gif",  
  footImageUrl: "/resource/image/common/dot_arrow2_bottom.gif"  
});
```

<a class="btn primary small round lowercase" id="btnStateStyles">상태별 배경색</a>

```js
gridView.setStateBar({
    mark:"text",
    styles:{font:"나눔고딕코딩"},
    stateStyles:{ 
        "updated":{"background":"#FF00FF00", font:"나눔고딕코딩"},
        "created":{"background":"#44FF22FF", figureBackground:"#88888888", font:"굴림체"},
        "deleted":{"background":"#44000000", foreground:"#FF88FF88", font:"바탕체"}
    }
});
```


<script>

  $('#btnSetVisibleFalse').click(function() {
    gridView.setStateBar({
      visible: false  
    });
  });

  $('#btnSetVisibleTrue').click(function() {
    gridView.setStateBar({
      visible: true  
    });
  });

  $('#btnSetRowState').click(function() {
    var curr = gridView.getCurrent();
    var rowState = $(":input:radio[name='rowState']:checked").val()
    dataProvider.setRowState(curr.dataRow, rowState)
  });

  $('#btnSetCheckBarText').click(function() {
    gridView.setStateBar({
        mark: "text",
        stateTexts: {
            created: "C",
            updated: "U",
            deleted: "D",
            createAndDeleted: "X"
        }
    });
  });

  $('#btnSetCheckBarDefault').click(function() {
    gridView.setStateBar({
        mark: "default"
    });
  });

  $('#btnSetText').click(function() {
    gridView.setStateBar({
      headText: "H",  
      footText: "F",
      headImageUrl: null,  
      footImageUrl: null  
    });
  });

  $('#btnSetImage').click(function() {
    gridView.setStateBar({
      headText: null,  
      footText: null,
      headImageUrl: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/dot_arrow2_top.gif",  
      footImageUrl: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/dot_arrow2_bottom.gif"  
    });
  });  

  $('#btnStateStyles').click(function() {
    gridView.setStateBar({
      mark:"text",
      styles:{font:"나눔고딕코딩"},
      stateStyles:{ 
          "updated":{"background":"#FF00FF00", font:"나눔고딕코딩"},
          "created":{"background":"#44FF22FF", figureBackground:"#88888888", font:"굴림체"},
          "deleted":{"background":"#44000000", foreground:"#FF88FF88", font:"바탕체"}
      }
    });
  });

</script>
