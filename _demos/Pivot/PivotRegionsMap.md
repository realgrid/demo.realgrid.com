---
layout: page
title: 피벗 영역
order: 15
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'Regions']
---

상세 영역 보기는 아래의 탭을 클릭하거나 최상위 요소탭 pivot 화면의 영역을 선택하면 해당 영역에 대한 상세 정보를 볼 수 있습니다.

<style type="text/css">
.document-formatting img {
	padding:0;
}
.area {
    background:#fff;
    display:block;
    height:475px;
    opacity:0;
    position:absolute;
    width:320px;
}
</style>

<script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
<script src="https://davidlynch.org/projects/maphilight/jquery.maphilight.min.js"></script>


<div id="container" style="width:1215px; height:496px;">
<img src="/resource/image/pivot_images/pivot_imagemap.png" id="imagemap" alt="" usemap="#Map" width="1215px" height="496px"/>
<map name="Map" id="Map">

    <area alt="" onmouseover="test()" title="" href="#contextMenu" shape="rect" coords="3,2,19,19" id="contextMenu" class="realpivot-title-menu"/>
    <area alt="" title="" href="#pivotSetup" shape="rect" coords="23,4,38,18" id="pivotSetup" class="realpivot-title-setup"/>
    <area alt="" title="" href="#pivotTitle" shape="rect" coords="3,4,161,21" id="pivotTitle" class="realpivot-cellreal pivot-title"/>

    <area alt="" title="" href="#tooltip" shape="rect" coords="234,197,339,266" id="tooltip" class="realpivot-tooltip"/>

    <area alt="" title="" href="#progressBar" shape="rect" coords="503,157,730,169" id="progressBar" class="realpivot-progress-bar"/>
    <area alt="" title="" href="#progressMessage" shape="rect" coords="503,174,728,185" id="progressMessage" class="realpivot-progress-message"/>
    <area alt="" title="" href="#progress" shape="rect" coords="492,150,740,193" id="progress" class="realpivot-progress"/>

    <area alt="" title="" href="#rowheaderSort" shape="rect" coords="67,64,78,73" id="rowHeaderSort1" class="realpivot-header-sort realpivot-header-sort-asc"/>
    <area alt="" title="" href="#rowheaderSort" shape="rect" coords="143,64,155,72" id="rowHeaderSort2" class="realpivot-header-sort realpivot-header-sort-asc"/>
    <area alt="" title="" href="#rowHeaderText" shape="rect" coords="5,61,156,74" id="rowHeaderText" class="realpivot-cell realpivot-row-header-text"/>
    <area alt="" title="" href="#rowHeader" shape="rect" coords="4,61,162,97" id="rowHeader" class="realpivot-cell realpivot-col-header"/>

    <area alt="" title="" href="#valueHeaderText" shape="rect" coords="3,26,155,37" id="valueHeaderText" class="realpivot-cell realpivot-value-header-text"/>
    <area alt="" title="" href="#valueHeader" shape="rect" coords="3,25,161,57" id="valueHeader" class="realpivot-cell realpivot-value-header"/>

    <area alt="" title="" href="#colHeaderSort" shape="rect" coords="226,7,237,16" id="colHeaderSort1" class="realpivot-header-sort realpivot-header-sort-asc"/>
    <area alt="" title="" href="#colHeaderSort" shape="rect" coords="303,7,315,17" id="colHeaderSort2" class="realpivot-header-sort realpivot-header-sort-asc"/>
    <area alt="" title="" href="#colHeaderText" shape="rect" coords="166,4,317,20" id="colHeaderText" class="realpivot-cell realpivot-col-header-text"/>
    <area alt="" title="" href="#colHeader" shape="rect" coords="164,3,1201,22" id="colHeader" class="realpivot-cell realpivot-col-header"/>

    <area alt="" title="" href="#colExpander-expand" shape="rect" coords="304,29,317,43" id="colExpander-expand1" class="realpivot-expander-expand"/>
    <area alt="" title="" href="#colExpander-expand" shape="rect" coords="863,27,878,42" id="colExpander-expand2" class="realpivot-expander-expand"/>
    <area alt="" title="" href="#colLabelGroup" shape="rect" coords="318,23,863,48" id="colLabelGroup1" class="realpivot-cell realpivot-col-label realpivot-col-d1 realpivot-col-group"/>
    <area alt="" title="" href="#colLabelGroup" shape="rect" coords="879,24,1203,46" id="colLabelGroup2" class="realpivot-cell realpivot-col-label realpivot-col-d1 realpivot-col-group"/>
    <area alt="" title="" href="#colSumTotal" shape="rect" coords="163,24,301,72" id="colSumTotal" class="realpivot-cell realpivot-col-sum realpivot-col-sum-tot"/>
    <area alt="" title="" href="#colSum" shape="rect" coords="161,72,443,97" id="colSum1" class="realpivot-cell realpivot-col-sum realpivot-col-sum-2"/>
    <area alt="" title="" href="#colSum" shape="rect" coords="864,72,1002,96" id="colSum2" class="realpivot-cell realpivot-col-sum realpivot-col-sum-2"/>
    <area alt="" title="" href="#colSum" shape="rect" coords="304,47,443,72" id="colSum3" class="realpivot-cell realpivot-col-sum realpivot-col-sum-2"/>
    <area alt="" title="" href="#colSum" shape="rect" coords="863,47,1002,70" id="colSum4" class="realpivot-cell realpivot-col-sum realpivot-col-sum-2"/>
    <area alt="" title="" href="#colLabel2" shape="rect" coords="444,46,861,70" id="colLabel2-1" class="realpivot-cell realpivot-col-label realpivot-col-d2"/>
    <area alt="" title="" href="#colLabel2" shape="rect" coords="1003,47,1200,70" id="colLabel2-2" class="realpivot-cell realpivot-col-label realpivot-col-d2"/>
    <area alt="" title="" href="#colLabel3" shape="rect" coords="444,72,862,97" id="colLabel3-1" class="realpivot-cell realpivot-col-label realpivot-col-d3"/>
    <area alt="" title="" href="#colLabel3" shape="rect" coords="1004,72,1201,96" id="colLabel3-2" class="realpivot-cell realpivot-col-label realpivot-col-d3"/>
    
    <area alt="" title="" href="#bodySumTotal" shape="rect" coords="163,99,303,483" id="bodySumTotal1" class="realpivot-cell realpivot-body-sum realpivot-body-sum-tot"/>
    <area alt="" title="" href="#bodySumTotal" shape="rect" coords="303,99,1203,121" id="bodySumTotal2" class="realpivot-cell realpivot-body-sum realpivot-body-sum-tot"/>

	<area alt="" title="" href="#bodySum" shape="rect" coords="301,124,443,482" id="bodySum1" class="realpivot-cell realpivot-body-sum"/>
	<area alt="" title="" href="#bodySum" shape="rect" coords="303,123,1202,146" id="bodySum2" class="realpivot-cell realpivot-body-sum"/>
    <area alt="" title="" href="#bodySum" shape="rect" coords="304,298,1203,320" id="bodySum3" class="realpivot-cell realpivot-body-sum"/>
    <area alt="" title="" href="#bodySum" shape="rect" coords="863,125,1001,484" id="bodySum4" class="realpivot-cell realpivot-body-sum"/>

	<area alt="" title="" href="#bodyValue" shape="rect" coords="443,149,863,296" id="bodyValue1" class="realpivot-cell realpivot-body-value"/>
	<area alt="" title="" href="#bodyValue" shape="rect" coords="1004,150,1203,295" id="bodyValue2" class="realpivot-cell realpivot-body-value"/>
    <area alt="" title="" href="#bodyValue" shape="rect" coords="443,326,860,484" id="bodyValue3" class="realpivot-cell realpivot-body-value"/>
    <area alt="" title="" href="#bodyValue" shape="rect" coords="1004,325,1199,481" id="bodyValue4" class="realpivot-cell realpivot-body-value"/>

    <area alt="" title="" href="#rowSumTotal" shape="rect" coords="3,99,163,123" id="rowSumTotal" class="realpivot-cell realpivot-row-sum realpivot-row-sum-tot"/>
    <area alt="" title="" href="#rowSumLevel" shape="rect" coords="74,123,163,147" id="rowSumLevel1" class="realpivot-cell realpivot-row-sum realpivot-row-sum-2"/>
    <area alt="" title="" href="#rowSumLevel" shape="rect" coords="74,298,163,321" id="rowSumLevel2" class="realpivot-cell realpivot-row-sum realpivot-row-sum-2"/>

    <area alt="" title="" href="#rowExpander-expand" shape="rect" coords="1,122,18,484" id="rowExpander-expand" class="realpivot-expander-expand"/>
    <area alt="" title="" href="#rowLabelGroup" shape="rect" coords="3,124,70,483" id="rowLabelGroup" class="realpivot-cell realpivot-row-label realpivot-row-d1 realpivot-row-group"/>
    <area alt="" title="" href="#rowLabelLevel" shape="rect" coords="72,149,161,295" id="rowLabelLevel1" class="realpivot-cell realpivot-row-label realpivot-row-d2"/>
    <area alt="" title="" href="#rowLabelLevel" shape="rect" coords="74,324,161,484" id="rowLabelLevel2" class="realpivot-cell realpivot-row-label realpivot-row-d2"/>
</map>
</div>
<div id="eventLog" style="width:100%; height:50px; border: 0px solid #5d8cc9; 
text-align:center;
font-weight: bold; 
font-style: italic;
font-size: 2.0em;
line-height: 1.0em"
><center></center></div>
<script>
function test(){

}

$("#contextMenu").click( function(event){
	classLog(event.currentTarget.className)
});
$("#pivotSetup").click( function(event){
	classLog(event.currentTarget.className)
});
$("#pivotTitle").click( function(event){
	classLog(event.currentTarget.className)
});
$("#tooltip").click( function(event){
	classLog(event.currentTarget.className)
});
$("#progress").click( function(event){
	classLog(event.currentTarget.className)
});
$("#progressBar").click( function(event){
	classLog(event.currentTarget.className)
});
$("#progressMessage").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowHeaderSort1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowHeaderSort2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowHeaderText").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowHeader").click( function(event){
	classLog(event.currentTarget.className)
});
$("#valueHeaderText").click( function(event){
	classLog(event.currentTarget.className)
});
$("#valueHeader").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colHeaderSort1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colHeaderSort2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colHeaderText").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colHeader").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colExpander-expand1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colExpander-expand2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colLabelGroup1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colLabelGroup2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colSumTotal").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colSum1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colSum2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colSum3").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colSum4").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colLabel2-1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colLabel2-2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colLabel3-1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#colLabel3-2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySumTotal1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySumTotal2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySum1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySum2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySum3").click( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySum4").click( function(event){
	classLog(event.currentTarget.className)
});
$("#bodyValue1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#bodyValue2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#bodyValue3").click( function(event){
	classLog(event.currentTarget.className)
});
$("#bodyValue4").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowSumTotal").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowSumLevel1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowSumLevel2").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowExpander-expand").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowLabelGroup").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowLabelLevel1").click( function(event){
	classLog(event.currentTarget.className)
});
$("#rowLabelLevel2").click( function(event){
	classLog(event.currentTarget.className)
});

function classLog(className){
	document.getElementById("eventLog").innerHTML = className
};



</script>