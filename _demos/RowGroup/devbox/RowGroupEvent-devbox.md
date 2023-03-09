#### 행 그룹핑 이벤트 확인하기

행 그룹을 접거나 펼칠 때 발생하는 이벤트들입니다.  
onExpanding, onCollapsing 이벤트에서는 false를 반환하면 접고 펼침이 되지 않습니다.

```js
gridView.onExpanded = function(grid, model) {
   addLog("onExpanded: {type:" + model.type + ", itemIndex: " + model.itemIndex + ", level: "+ model.level + "}");
};
gridView.onExpanding = function(grid, model) {
   addLog("onExpanding: {type:" + model.type + ", itemIndex: " + model.itemIndex + ", level: "+ model.level + "}");
   //return false;
};
gridView.onCollapsed = function(grid, model) {
   addLog("onCollapsed: {type:" + model.type + ", itemIndex: " + model.itemIndex + ", level: "+ model.level + "}");
};
gridView.onCollapsing = function(grid, model) {
   addLog("onCollapsing: {type:" + model.type + ", itemIndex: " + model.itemIndex + ", level: "+ model.level + "}");
   //return false;
};
```