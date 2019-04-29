#### 다중 아이콘 렌더러

[multiIconCellRenderer](http://help.realgrid.com/api/types/MultiIconCellRenderer/) 셀에 여러개의 icon과 Text를 표시할 수 있습니다.

```js
renderer: {
    type:"multiIcon",
    icons: ['/resource/image/icon/be.png', '/resource/image/icon/br.png']
    ...
});
```

#### 동적 아이콘 렌더러

renderCallback 으로 특정 값에 따라 동적으로 아이콘을 표시할 수 있습니다.

```js
renderer: {
    type:"multiIcon",
    renderCallback:function(grid, index) {
      var value = grid.getValue(index.itemIndex, index.fieldName);
      var ret = [];
      if (value == "10248") {
        ret.push('/resource/image/icon/be.png');
      }else {
        ret.push('/resource/image/icon/br.png');
      }

      return ret
    }
});
```