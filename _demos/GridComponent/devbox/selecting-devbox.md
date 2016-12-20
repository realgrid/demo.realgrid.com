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

<script>

  $('#btnSetNone').click(function() {
    gridView.setFixedOptions({
      style: 'none'
    });
  });


  $('#btnSetRows').click(function() {
    gridView.setFixedOptions({
      style: 'rows'
    });
  });


  $('#btnSetColumns').click(function() {
    gridView.setFixedOptions({
      style: 'columns'
    });
  });

  $('#btnSetSingleRow').click(function() {
    gridView.setFixedOptions({
      style: 'singleRow'
    });
  });

  $('#btnSetSingleColumn').click(function() {
    gridView.setFixedOptions({
      style: 'singleColumn'
    });
  });

</script>
