#### scrollMessageCallback

[gridView.displayOptions()](http://help.realgrid.com/api/types/DisplayOptions/)의 scrollMessageCallback 으로 가로스크롤 시 표시할 값을 설정합니다.

```
<style type="text/css">
.rg-scroll-tip-view {
  border: 1px solid red;
  background: white;
  font-size: 12px;
  white-space: nowrap;
  border-radius: 4px;
}
</style>

gridView.setDisplayOptions({
    liveScroll: false,
    scrollMessageCallback:function(grid, vertical, itemIndex) {
        console.log(itemIndex)
        if (vertical === "vertical") {
            var dataRow = grid.getDataRow(itemIndex); 
            if (dataRow >= 0) {
                return "<span style='color:red'>"+ (itemIndex + 1) +"</span>"
            }
        }
    }
});
```