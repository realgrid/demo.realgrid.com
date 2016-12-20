#### 왼쪽 열 고정
[FixedOptions](http://help.realgrid.com/api/types/FixedOptions/)의 속성중 colCount를 지정하여 왼쪽 열부터 열 고정을 할 수 있습니다. 

<a class="btn primary small round lowercase" id="btnSetColCount">왼쪽 열 고정</a>

```js
gridView.setFixedOptions({
  colCount: 2
});
```

#### 오른쪽 열 고정
[FixedOptions](http://help.realgrid.com/api/types/FixedOptions/)의 속성중 rightColCount를 지정하여 마지막 열부터 열 고정을 할 수 있습니다.  

<a class="btn primary small round lowercase" id="btnSetRightColCount">오른쪽 열 고정</a>

```js
gridView.setFixedOptions({
  rightColCount: 1
});
```

<script>

  $('#btnSetColCount').click(function() {
    gridView.setFixedOptions({
      colCount: 2
    });
  });

  $('#btnSetRightColCount').click(function() {
    gridView.setFixedOptions({
      rightColCount: 1
    });
  });  
</script>
