#### 아이템 모델

각 아이템은 표시되는 순서대로 index 값을 갖게 되는데, 리얼그리드 대부분의 함수들은 이 index 값을 전달하여 실행됩니다.  
하지만, 표시되지 않는 아이템들 예를 들어 ,감춰진 RowGroup의 아이템들이나 감춰진 Tree 아이템들은 이 index를 통해 접근할 수 없습니다.  
이런 경우 등을 위해 Flash 그리드 내부의 아이템 모델 정보를 리턴하고 그 정보로 다른 모델 정보를 얻어올 수 있는 함수들을 제공합니다.


#### 아이템 모델의 종류와 리턴

아이템 모델의 종류는 아래와 같습니다.

```js
var ItemType = {
    ROW: "row",         // 데이터 행
    GROUP: "group",     // 그룹 (그룹 Header로 표시됩니다)
    FOOTER: "footer",   // 그룹 Footer
    TREE: "tree"        // 트리 노드 ("group" 이기도 합니다)
};
```

아이템 모델 정보는 아래와 같은 형태로 리턴 됩니다.

```js
{
    type: "row",        // ItemType
    itemIndex: 0,       // 아이템 index
    dataRow: -1,        // 아이템에 연결된 데이터행. type이 "row"가 아니면 -1
    checked: false,     // 아이템 checked 여부
    id: 0,              // 내부 사용 아이디,
    parentId: 0,        // 내부 사용 아이디,
    footerId: 0,        // 내부 사용 아이디
};
```

모델관련 API호출시 extended를 true로 지정시 반환되는 확장 모델정보에 다음과 같은 정보가 추가됩니다.

```js
level: 2,        // 계층 구조상 Level, 1부터 시작
childIndex: 0,   // 부모 모델내의 순서
```

#### 아이템 모델 가져오기

<input type="checkbox" id="chkExtendedModel"> 
extended(확장정보 포함 여부)

 
<a class="btn primary small round lowercase" id="btnGetModel">getModel</a>  
[getModel()](http://help.realgrid.com/api/GridBase/getModel/)함수는 아이템 index에 해당하는 아이템모델을 리턴 합니다.  
```js
var extended = $("#chkExtendedModel").is(":checked");
var itemIndex = gridView.getCurrent().itemIndex;
var item = gridView.getModel(itemIndex, extended);
alert(JSON.stringify(item));
```

<a class="btn primary small round lowercase" id="btnGetParentModel">getParentModel</a>  
[getParentModel()](http://help.realgrid.com/api/GridBase/getParentModel/)함수는 아이템 모델의 부모 아이템 모델을 리턴 합니다.  
```js
var extended = $("#chkExtendedModel").is(":checked");
var idx = gridView.getCurrent();
var item = gridView.getModel(idx.itemIndex);
var parent = gridView.getParentModel(item,extended);
alert(JSON.stringify(item));
if (parent) {
    idx.itemIndex = parent.itemIndex;
    gridView.setCurrent(idx);
}
```

<a class="btn primary small round lowercase" id="btnGetRootModel">getRootModel</a>  
[getRootModel()](http://help.realgrid.com/api/GridBase/getRootModel/)함수는 아이템 모델의 최상위 조상 아이템 모델을 리턴 합니다.  
```js
var extended = $("#chkExtendedModel").is(":checked");
var idx = gridView.getCurrent();
var item = gridView.getModel(idx.itemIndex);
var root = gridView.getRootModel(item, extended);
console.log(JSON.stringify(root));
alert(JSON.stringify(root));
if (root) {
    idx.itemIndex = root.itemIndex;
    gridView.setCurrent(idx);
}
```
 
<a class="btn primary small round lowercase" id="btnGetChildModels">getChildModels</a>  
[getChildModels()](http://help.realgrid.com/api/GridBase/getChildModels/)함수는 아이템 모델의 바로 아래 자식 아이템 모델들을 리턴 합니다. 
```js
var extended = $("#chkExtendedModel").is(":checked");
var itemIndex = gridView.getCurrent().itemIndex;
var item = gridView.getModel(itemIndex);
if (item) {
    var children = gridView.getChildModels(item,extended);
    alert(JSON.stringify(children));
}
```

<a class="btn primary small round lowercase" id="btnGetChildModel">getChildModel</a>  
[getChildModel()](http://help.realgrid.com/api/GridBase/getChildModel/)함수는 아이템 모델의 자식 아이템 모델을 리턴 합니다.  
```js
var extended = $("#chkExtendedModel").is(":checked");
var itemIndex = gridView.getCurrent().itemIndex;
var group = gridView.getModelAs(itemIndex, "group");
if (group && group.count > 0) {
    var item = gridView.getChildModel(group, 0, extended);
    alert(JSON.stringify(item));
}
```
 
<a class="btn primary small round lowercase" id="btnGetModels">getModels</a>  
[getModels()](http://help.realgrid.com/api/GridBase/getModels/)함수는 지정한 아이템 index들에 해당하는 아이템 모델들을 배열로 리턴 합니다. 
```js
var extended = $("#chkExtendedModel").is(":checked");
var items = gridView.getModels([0, 1, 2], extended);
var s = JSON.stringify(items);
alert(JSON.stringify(s));
```
 
<a class="btn primary small round lowercase" id="btnGetModelOfRow">getModelOfRow</a>  
[getModelOfRow()](http://help.realgrid.com/api/GridBase/getModelOfRow/)함수는 지정한 데이터 행에 해당하는 아이템 모델을 리턴 합니다. 
```js
var extended = $("#chkExtendedModel").is(":checked");
var row = gridView.getCurrent().dataRow;
var item = gridView.getModelOfRow(row,extended);
alert(JSON.stringify(item));
```
 
<a class="btn primary small round lowercase" id="btnGetModelsOfRows">getModelsOfRows</a>  
[getModelsOfRows()](http://help.realgrid.com/api/GridBase/getModelsOfRows/)함수는 지정한 데이터 행들에 해당하는 아이템 모델들을 배열로 리턴 합니다. 
```js
var extended = $("#chkExtendedModel").is(":checked");
var items = gridView.getModelsOfRows([0, 1, 2],extended);
var s = JSON.stringify(items);
alert(JSON.stringify(s));
```
 
<a class="btn primary small round lowercase" id="btnGetGroupSummary">getGroupSummary</a>  
[getGroupSummary](http://help.realgrid.com/api/GridBase/getGroupSummary/)	지정한 그룹아이템 모델의 합계 정보를 리턴 합니다.  
```js
var idx = gridView.getCurrent();
var item = gridView.getModelAs(idx.itemIndex, "row");
     
if (item) {
    var group = gridView.getParentModel(item);
         
    if (group && idx.fieldIndex >= 0) {
        var summary = gridView.getGroupSummary(group, idx.fieldIndex);
        if (summary) {
            alert(JSON.stringify(summary));
        }
    }
}
```
  
<a class="btn primary small round lowercase" id="btnExpandModel">expandModel</a>  
지정한 그룹아이템 모델을 expand 합니다. 
```js
var recursive = $("#chkExpandRecursive").is(":checked");
var force = $("#chkExpandForce").is(":checked");
var itemIndex = gridView.getCurrent().itemIndex;
var group = gridView.getModelAs(itemIndex, "group");
if (group) {
    gridView.expandModel(group, recursive, force);
}
```
 
<a class="btn primary small round lowercase" id="btnCollapseModel">collapseModel</a>  
collapseModel	지정한 그룹아이템 모델을 collapse 합니다. 
```js
var recursive = $("#chkCollapseRecursive").is(":checked");
    var itemIndex = gridView.getCurrent().itemIndex;
    var group = gridView.getModelAs(itemIndex, "group");
    if (group) {
        gridView.collapseModel(group, recursive);
    }
```


#### `주의`

* 대량의 아이템 모델을 리턴하는 함수는 메모리 사용이나 속도면에서 부담을 줄 수 있으므로, 아이템 index로 해결할 수 있는 경우라면 `반드시 index 함수들을 사용`해야 합니다.  
특히 확장모델정보는 저장된 값이 아니라 그때마다 계산하여 가져오는 방식이므로 더많은 부담을 줄 수 있습니다.
* 함수들에서 리턴된 모델을 다른 함수의 매개변수로 전달하게 되므로 속성 값을 수정해서는 안됩니다.   
특히, 내부 사용 아이디들은 의미있는 값으로 사용해서도 안됩니다.
* 데이터의 변경이나 혹은 Row Grouping이 새로 실행될 때, 혹은 다른 이유로 그리드나 트리의 아이템모델은 자주 갱신됩니다.   
대개의 경우 리턴된 아이템모델을 하나의 함수 밖에서 재사용하기 위해 저장하는 것은 의미가 없고 위험할 수 있습니다.

<script>
$('#btnGetModel').click(function() {
    var extended = $("#chkExtendedModel").is(":checked");
    var itemIndex = gridView.getCurrent().itemIndex;
    var item = gridView.getModel(itemIndex, extended);
    console.log(JSON.stringify(item));
    alert(JSON.stringify(item));
});
 
$('#btnGetParentModel').click(function() {
    var extended = $("#chkExtendedModel").is(":checked");
    var idx = gridView.getCurrent();
    var item = gridView.getModel(idx.itemIndex);
    var parent = gridView.getParentModel(item,extended);
    console.log(JSON.stringify(parent));
    alert(JSON.stringify(item));
    if (parent) {
        idx.itemIndex = parent.itemIndex;
        gridView.setCurrent(idx);
    }
});
 
$('#btnGetRootModel').click(function() {
    var extended = $("#chkExtendedModel").is(":checked");
    var idx = gridView.getCurrent();
    var item = gridView.getModel(idx.itemIndex);
    var root = gridView.getRootModel(item, extended);
    console.log(JSON.stringify(root));
    alert(JSON.stringify(root));
    if (root) {
        idx.itemIndex = root.itemIndex;
        gridView.setCurrent(idx);
    }
});
 
$('#btnGetChildModels').click(function() {
    var extended = $("#chkExtendedModel").is(":checked");
    var itemIndex = gridView.getCurrent().itemIndex;
    var item = gridView.getModel(itemIndex);
    if (item) {
        var children = gridView.getChildModels(item,extended);
        console.log(JSON.stringify(children));
        alert(JSON.stringify(children));
    }
});
 
$('#btnGetChildModel').click(function() {
    var extended = $("#chkExtendedModel").is(":checked");
    var itemIndex = gridView.getCurrent().itemIndex;
    var group = gridView.getModelAs(itemIndex, "group");
    if (group && group.count > 0) {
        var item = gridView.getChildModel(group, 0, extended);
        console.log(JSON.stringify(item));
        alert(JSON.stringify(item));
    }
});
 
$('#btnGetModels').click(function() {
    var extended = $("#chkExtendedModel").is(":checked");
    var items = gridView.getModels([0, 1, 2], extended);
    var s = JSON.stringify(items);
    console.log(s);
    alert(JSON.stringify(s));
});
 
$('#btnGetModelOfRow').click(function() {
    var extended = $("#chkExtendedModel").is(":checked");
    var row = gridView.getCurrent().dataRow;
    var item = gridView.getModelOfRow(row,extended);
    console.log(JSON.stringify(item));
    alert(JSON.stringify(item));
});
 
$('#btnGetModelsOfRows').click(function() {
    var extended = $("#chkExtendedModel").is(":checked");
    var items = gridView.getModelsOfRows([0, 1, 2],extended);
    var s = JSON.stringify(items);
    console.log(s);
    alert(JSON.stringify(s));
});
 
$('#btnGetGroupSummary').click(function() {
    var idx = gridView.getCurrent();
    var item = gridView.getModelAs(idx.itemIndex, "row");
         
    if (item) {
        var group = gridView.getParentModel(item);
             
        if (group && idx.fieldIndex >= 0) {
            var summary = gridView.getGroupSummary(group, idx.fieldIndex);
            if (summary) {
                console.log(JSON.stringify(summary));
                alert(JSON.stringify(summary));
            }
        }
    }
});
 
$('#btnExpandModel').click(function() {
    var recursive = $("#chkExpandRecursive").is(":checked");
    var force = $("#chkExpandForce").is(":checked");
    var itemIndex = gridView.getCurrent().itemIndex;
    var group = gridView.getModelAs(itemIndex, "group");
    if (group) {
        gridView.expandModel(group, recursive, force);
    }
});
 
$('#btnCollapseModel').click(function() {
    var recursive = $("#chkCollapseRecursive").is(":checked");
    var itemIndex = gridView.getCurrent().itemIndex;
    var group = gridView.getModelAs(itemIndex, "group");
    if (group) {
        gridView.collapseModel(group, recursive);
    }
});
</script>