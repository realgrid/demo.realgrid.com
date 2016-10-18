---
layout: page
title: 컬럼 만들기
order : 1
devbox: true
devboxfile: SetColumns.md
categories: columns
---

<div id="realgrid" style="width:100%; height:300px"></div>

<script>
  var gridView;
  var dataProvider;

  $(document).ready( function(){
      RealGridJS.setRootContext("/lib/realgrid/realgridjs_eval.1.1.19");

      dataProvider = new RealGridJS.LocalDataProvider();
      gridView = new RealGridJS.GridView("realgrid");
      gridView.setDataSource(dataProvider);    
  });   
</script>
