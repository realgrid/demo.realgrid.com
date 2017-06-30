#### 선택 스타일을 BLOCK으로

[SelectOptions](http://help.realgrid.com/api/types/SelectOptions/)의 속성중 style을 `block`로 지정하면 선택 영역을 블럭으로 지정할 수 있습니다.  

<a class="btn primary small round lowercase" id="btnSetBlock">BLOCK</a>

```js
gridView.setSelectOptions({
  style: 'block'
});
```

#### 선택 스타일을 ROWS로

[SelectOptions](http://help.realgrid.com/api/types/SelectOptions/)의 속성중 style을 `rows`로 지정하면 선택 영역을 여러 행으로 지정할 수 있습니다.  

<a class="btn primary small round lowercase" id="btnSetRows">ROWS</a>

```js
gridView.setSelectOptions({
  style: 'rows'
});
```

#### 선택 스타일을 COLUMNS로

[SelectOptions](http://help.realgrid.com/api/types/SelectOptions/)의 속성중 style을 `columns`로 지정하면 선택 영역을 여러 컬럼으로 지정할 수 있습니다.  

<a class="btn primary small round lowercase" id="btnSetColumns">COLUMNS</a>

```js
gridView.setSelectOptions({
  style: 'columns'
});
```

#### 선택 스타일을 SINGLE ROW로

[SelectOptions](http://help.realgrid.com/api/types/SelectOptions/)의 속성중 style을 `singleRow`로 지정하면 선택 영역을 하나의 행만 지정할 수 있습니다.  

<a class="btn primary small round lowercase" id="btnSetSingleRow">SINGLE ROW</a>

```js
gridView.setSelectOptions({
  style: 'singleRow'
});
```

#### 선택 스타일을 SINGLE COLUMN으로

[SelectOptions](http://help.realgrid.com/api/types/SelectOptions/)의 속성중 style을 `singleColumn`로 지정하면 선택 영역을 하나의 컬럼만 지정할 수 있습니다.  

<a class="btn primary small round lowercase" id="btnSetSingleColumn">SINGLE COLUMN</a>

```js
gridView.setSelectOptions({
  style: 'singleColumn'
});
```

#### 선택 스타일을 NONE으로

[SelectOptions](http://help.realgrid.com/api/types/SelectOptions/)의 속성중 style을 `none`로 지정하면 선택 영역을 아무것도 지정할 수 없게 할 수 있습니다.  

<a class="btn primary small round lowercase" id="btnSetNone">NONE</a>

```js
gridView.setSelectOptions({
  style: 'none'
});
```

#### 선택된 셀의 행 표시

[DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/).rowFocusVisible 을 True로 설정하여 선택된 셀의 행을 표시할 수 있습니다. 위에 설명된 선택 스타일들과 중첩으로 사용 가능하며 반드시 rowFocusBackground 속성에 색상값을 지정해야 합니다.  
<a class="btn primary small round lowercase" id="btnSetRowFocusVisible">rowFocusVisible</a>

```js
gridView.setDisplayOptions({
  rowFocusVisible:true, 
  rowFocusBackground:"#340000ff"
});
```

#### rowHoverMask

현재 마우스가 위치한 지점의 hoverMask속성에 따른 영역의 배경색상을 표시할 수 있습니다.  

<a class="btn primary small round lowercase" id="btnSetRowHoverMask">행 단위 hoverMask 설정</a>

```js
gridView.setDisplayOptions({
  rowHoverMask:{
    visible:true,
    styles:{
      background:"#2065686b"
    },
    hoverMask:"row"
  }
});
```

<script>
  $('#btnSetBlock').click(function() {
    gridView.setSelectOptions({
      style: 'block'
    });
  });

  $('#btnSetNone').click(function() {
    gridView.setSelectOptions({
      style: 'none'
    });
  });


  $('#btnSetRows').click(function() {
    gridView.setSelectOptions({
      style: 'rows'
    });
  });


  $('#btnSetColumns').click(function() {
    gridView.setSelectOptions({
      style: 'columns'
    });
  });

  $('#btnSetSingleRow').click(function() {
    gridView.setSelectOptions({
      style: 'singleRow'
    });
  });

  $('#btnSetSingleColumn').click(function() {
    gridView.setSelectOptions({
      style: 'singleColumn'
    });
  });

  $('#btnSetRowFocusVisible').click(function() {
    gridView.setDisplayOptions({
      rowFocusVisible:true, 
      rowFocusBackground:"#340000ff"
    });
  });

  $('#btnSetRowHoverMask').click(function() {
    gridView.setDisplayOptions({
      rowHoverMask:{
        visible:true,
        styles:{
          background:"#2065686b"
        },
        hoverMask:"row"
      }
    });
  });
</script>
