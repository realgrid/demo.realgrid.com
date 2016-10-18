---
layout: page
title: 컬럼 속성 변경하기
order: 2
categories: Columns
---

<div id="realgrid" style="width:100%; height:300px"></div>

<script>
  var gridView;
  var dataProvider;

  $(document).ready( function(){
      RealGridJS.setRootContext("{{ "/lib/realgrid/realgridjs_eval.1.1.19" | prepend: site.baseurl }}");

      dataProvider = new RealGridJS.LocalDataProvider();
      gridView = new RealGridJS.GridView("realgrid");
      gridView.setDataSource(dataProvider);    
  });   
</script>
