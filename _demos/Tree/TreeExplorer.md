---
layout: page
title: 파일 탐색기 샘플
order: 10
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---

<script>
  var onDoneStyleSet = function() {
    var dataUrl = '{{ "/resource/data/treeOrgData1.json" | prepend: site.baseurl }}';
    $.ajax({
        url: dataUrl,
        success: function(data) {
          treeDataProvider.setJsonRows(data, "rows","","");
        }
    });
  }
</script>

<div class="row">
  <div class="col-md-4 col-sm-4">
    {% include realtree.html
      treeVar="treeView"
      dpVar="treeDataProvider"
      fieldSet="treeOrgFields1"
      columnSet="treeOrgColumns1"
      dpOptionSet="treeDataProviderOption1"
      treeOptionSet="treeOrgOption1"
      styleSet="treeOrgStyles1"
      doneStyleSet="onDoneStyleSet"
      
      treeId="realtree"
      treeField="tree"
      needSorting="true"
      childrenField=""
      iconField="icon"
      showToolbox="true"
      treeWidth="100%"
      treeHeight="300px" %}
  </div>
  <div class="col-md-8 col-sm-8">
    {% include realgrid.html
      gridVar="gridView"
      dpVar="dataProvider"
      fieldSet="fieldset1"
      columnSet="columnset1"
      dpOptionSet="dataProviderOption1"
      gridOptionSet="gridOption1"
      styleSet="defaultStyle"
      dataSet="griddata1"
      gridId="realgrid"
      showToolbox="true"
      gridWidth="100%"
      gridHeight="300px" %}
  </div>
</div>
