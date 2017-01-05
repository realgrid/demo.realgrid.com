#### 행 병합 그루핑

 [행 그룹핑](/demo/RowGroup/RowGrouping/)과 마찬가지로 그룹마다 Header나 Footer를 추가하여 표시할 수 있습니다.  
 마찬가지로, 그룹 헤더에 표시할 텍스트는 `rowGroup.headerStatement` 속성으로 지정하고, 각 Footer 셀에 표시할 값은 `Column.footer.groupExpression`으로 지정할 수 있습니다. 


#### RowGroup 설정

[setRowGroup()](http://help.realgrid.com/api/GridBase/setRowGroup/)함수는 그리드 RowGroup과 관련된 정보들을 설정합니다.  

rowGrouping 상태일 때 그룹의 펼침 또는 접힘 상태에 따라 그룹푸터와 그룹헤더의 표시방법을 설정 할 수 있습니다.

**자식들이 `표시`되고 있을 때**  
<input type="radio" name="expanded" value="footer" checked="checked">
<label style="vertical-align:middle">FOOTER</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="expanded" value="header">
<label style="vertical-align:middle">HEADER</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="expanded" value="both">
<label style="vertical-align:middle">BOTH</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="expanded" value="none">
<label style="vertical-align:middle">NONE</label>

```js
gridView.setRowGroup({
    expandedAdornments: $(':radio[name="expanded"]:checked').val()
});
```

*자식들이 `감춰진 상태`일 때*  
<input type="radio" name="collapsed" value="footer" checked="checked">
<label style="vertical-align:middle">FOOTER</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="collapsed" value="header">
<label style="vertical-align:middle">HEADER</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="collapsed" value="both">
<label style="vertical-align:middle">BOTH</label>


```js
gridView.setRowGroup({
    collapsedAdornments: $(':radio[name="collapsed"]:checked').val()
});
```

*Expander 표시*   
<input type="radio" name="expander" value="true" checked="checked">
<label style="vertical-align:middle">표시</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="expander" value="">
<label style="vertical-align:middle">감춤</label>


```js
gridView.setRowGroup({
    mergeExpander: $(':radio[name="expander"]:checked').val()
});
```


#### 제한 사항

병합 모드에서 제한 되는 부분은 아래와 같습니다.  

* Grouping 된 컬럼은 순서대로 그리드 앞쪽 순서대로 배치됩니다.
* Grouping 된 컬럼은 위치를 변경할 수 없습니다.


<script>
$(":radio[name='expanded']").change(expandedAdornmentsChange);
$(":radio[name='collapsed']").change(collapsedAdornmentsChange);
$(":radio[name='expander']").change(expanderChange);

function expandedAdornmentsChange(e) {
    gridView.setRowGroup({
        expandedAdornments: $(':radio[name="expanded"]:checked').val()
    });
}
 
function collapsedAdornmentsChange(e) {
    gridView.setRowGroup({
        collapsedAdornments: $(':radio[name="collapsed"]:checked').val()
    });
}
 
function expanderChange(e) {
    gridView.setRowGroup({
        mergeExpander: $(':radio[name="expander"]:checked').val()
    });
}
</script>