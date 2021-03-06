---
layout: page
title: 피벗 영역
order: 15
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'Regions']
---

pivot 이미지 영역에 마우스를 올리면 해당 영역의 className과 영역을 확인 할 수 있습니다.

<style type="text/css">
.document-formatting img {
	padding:0;
}
</style>

<script src="/lib/jquery/jquery-1.11.2.min.js"></script>
<script src="/lib/jquery/jquery.maphilight.min.js"></script>

<script type="text/javascript">
	$(function() {
		$('.map').maphilight({fade: true});
		$('.setupBox').maphilight({fade: true});
	});
</script>
<!-- pivot -->
<div id="container" style="width:1019px; height:503px;">
	<img class="map" src="/resource/image/pivot_images/pivot_imagemap3.png" id="imagemap" alt="" usemap="#Map2" width="1019px" height="503px"/>
	<map name="Map2" id="Map2">

	    <area alt="" title="" href="#contextMenu" shape="rect" coords="5,3,21,21" id="contextMenu" class="realpivot-title-menu"/>
	    <area alt="" title="" href="#pivotSetup" shape="rect" coords="22,3,40,20" id="pivotSetup" class="realpivot-title-setup"/>
	    <area alt="" title="" href="#pivotTitle" shape="rect" coords="4,2,163,22" id="pivotTitle" class="realpivot-cell realpivot-title"/>

	    <area alt="" title="" href="#tooltip" shape="rect" coords="165,224,267,293" id="tooltip" class="realpivot-tooltip"/>

	    <area alt="" title="" href="#progressBar" shape="rect" coords="394,157,623,170" id="progressBar" class="realpivot-progress-bar"/>
	    <area alt="" title="" href="#progressMessage" shape="rect" coords="396,171,621,186" id="progressMessage" class="realpivot-progress-message"/>
	    <area alt="" title="" href="#progress" shape="rect" coords="384,146,635,194" id="progress" class="realpivot-progress"/>

	    <area alt="" title="" href="#rowheaderSort" shape="rect" coords="68,65,79,75" id="rowHeaderSort1" class="realpivot-header-sort realpivot-header-sort-asc"/>
	    <area alt="" title="" href="#rowheaderSort" shape="rect" coords="143,63,156,74" id="rowHeaderSort2" class="realpivot-header-sort realpivot-header-sort-desc"/>
	    <area alt="" title="" href="#rowHeaderText" shape="rect" coords="5,61,158,78" id="rowHeaderText" class="realpivot-cell realpivot-row-header-text"/>
	    <area alt="" title="" href="#rowHeader" shape="rect" coords="4,61,163,98" id="rowHeader" class="realpivot-cell realpivot-row-header"/>

	    <area alt="" title="" href="#valueHeaderText" shape="rect" coords="6,25,159,39" id="valueHeaderText" class="realpivot-cell realpivot-value-header-text"/>
	    <area alt="" title="" href="#valueHeader" shape="rect" coords="4,24,162,58" id="valueHeader" class="realpivot-cell realpivot-value-header"/>

	    <area alt="" title="" href="#colHeaderSort" shape="rect" coords="226,6,239,18" id="colHeaderSort1" class="realpivot-header-sort realpivot-header-sort-asc"/>
	    <area alt="" title="" href="#colHeaderSort" shape="rect" coords="304,6,316,18" id="colHeaderSort2" class="realpivot-header-sort realpivot-header-sort-asc"/>
	    <area alt="" title="" href="#colHeaderText" shape="rect" coords="167,3,320,19" id="colHeaderText" class="realpivot-cell realpivot-col-header-text"/>
	    <area alt="" title="" href="#colHeader" shape="rect" coords="164,2,1001,21" id="colHeader" class="realpivot-cell realpivot-col-header"/>

	    <area alt="" title="" href="#colExpander-expand" shape="rect" coords="304,23,319,47" id="colExpander-expand1" class="realpivot-expander-expand"/>
	    <area alt="" title="" href="#colExpander-expand" shape="rect" coords="863,23,880,46" id="colExpander-expand2" class="realpivot-expander-expand"/>
	    <area alt="" title="" href="#colLabelGroup" shape="rect" coords="305,24,865,49" id="colLabelGroup1" class="realpivot-cell realpivot-col-label realpivot-col-d1 realpivot-col-group"/>
	    <area alt="" title="" href="#colLabelGroup" shape="rect" coords="865,24,1000,49" id="colLabelGroup2" class="realpivot-cell realpivot-col-label realpivot-col-d1 realpivot-col-group"/>
	    <area alt="" title="" href="#colSumTotal" shape="rect" coords="162,22,304,73" id="colSumTotal" class="realpivot-cell realpivot-col-sum realpivot-col-sum-tot"/>
	    <area alt="" title="" href="#colSum" shape="rect" coords="163,72,443,98" id="colSum1" class="realpivot-cell realpivot-col-sum realpivot-col-sum-2"/>
	    <area alt="" title="" href="#colSum" shape="rect" coords="864,74,999,98" id="colSum2" class="realpivot-cell realpivot-col-sum realpivot-col-sum-2"/>
	    <area alt="" title="" href="#colSum" shape="rect" coords="305,49,445,74" id="colSum3" class="realpivot-cell realpivot-col-sum realpivot-col-sum-2"/>
	    <area alt="" title="" href="#colSum" shape="rect" coords="864,48,1000,74" id="colSum4" class="realpivot-cell realpivot-col-sum realpivot-col-sum-2"/>
	    <area alt="" title="" href="#colLabel2" shape="rect" coords="444,49,864,73" id="colLabel2-1" class="realpivot-cell realpivot-col-label realpivot-col-d2"/>
	    <area alt="" title="" href="#colLabel3" shape="rect" coords="444,72,862,98" id="colLabel3-1" class="realpivot-cell realpivot-col-label realpivot-col-d3"/>
	    
	    <area alt="" title="" href="#bodySumTotal" shape="rect" coords="163,99,303,483" id="bodySumTotal1" class="realpivot-cell realpivot-body-sum realpivot-body-sum-tot"/>
	    <area alt="" title="" href="#bodySumTotal" shape="rect" coords="304,99,998,122" id="bodySumTotal2" class="realpivot-cell realpivot-body-sum realpivot-body-sum-tot"/>

		<area alt="" title="" href="#bodySum" shape="rect" coords="304,124,1001,147" id="bodySum1" class="realpivot-cell realpivot-body-sum"/>
	    <area alt="" title="" href="#bodySum" shape="rect" coords="305,299,1001,323" id="bodySum2" class="realpivot-cell realpivot-body-sum"/>
	    <area alt="" title="" href="#bodySum" shape="rect" coords="303,324,999,347" id="bodySum3" class="realpivot-cell realpivot-body-sum"/>
	    <area alt="" title="" href="#bodySum" shape="rect" coords="304,124,443,483" id="bodySum4" class="realpivot-cell realpivot-body-sum"/>
	    <area alt="" title="" href="#bodySum" shape="rect" coords="865,123,1001,483" id="bodySum5" class="realpivot-cell realpivot-body-sum"/>

		<area alt="" title="" href="#bodyValue" shape="rect" coords="445,148,863,299" id="bodyValue1" class="realpivot-cell realpivot-body-value"/>
	    <area alt="" title="" href="#bodyValue" shape="rect" coords="444,347,865,485" id="bodyValue2" class="realpivot-cell realpivot-body-value"/>

	    <area alt="" title="" href="#rowSumTotal" shape="rect" coords="3,99,163,123" id="rowSumTotal" class="realpivot-cell realpivot-row-sum realpivot-row-sum-tot"/>
	    <area alt="" title="" href="#rowSumLevel" shape="rect" coords="74,124,164,147" id="rowSumLevel1" class="realpivot-cell realpivot-row-sum realpivot-row-sum-2"/>
	    <area alt="" title="" href="#rowSumLevel" shape="rect" coords="74,298,164,323" id="rowSumLevel2" class="realpivot-cell realpivot-row-sum realpivot-row-sum-2"/>
	    <area alt="" title="" href="#rowSumLevel" shape="rect" coords="74,324,164,346" id="rowSumLevel3" class="realpivot-cell realpivot-row-sum realpivot-row-sum-2"/>

	    <area alt="" title="" href="#rowExpander-expand" shape="rect" coords="4,124,18,298" id="rowExpander-expand1" class="realpivot-expander-expand"/>
	    <area alt="" title="" href="#rowExpander-expand" shape="rect" coords="4,323,18,483" id="rowExpander-expand2" class="realpivot-expander-expand"/>
	    <area alt="" title="" href="#rowExpander-collapse" shape="rect" coords="4,298,18,323" id="rowExpander-collapse" class="realpivot-expander-collapse"/>
	    <area alt="" title="" href="#rowLabelGroup" shape="rect" coords="4,123,72,485" id="rowLabelGroup" class="realpivot-cell realpivot-row-label realpivot-row-d1 realpivot-row-group"/>
	    <area alt="" title="" href="#rowLabelLevel" shape="rect" coords="74,148,163,297" id="rowLabelLevel1" class="realpivot-cell realpivot-row-label realpivot-row-d2"/>
	    <area alt="" title="" href="#rowLabelLevel" shape="rect" coords="74,349,162,483" id="rowLabelLevel2" class="realpivot-cell realpivot-row-label realpivot-row-d2"/>

	    <area alt="" title="" href="#" shape="rect" coords="4,485,23,500" id="realpivot-hsbar1" class="realpivot-sbar-button realpivot-sbar-hnbutton"/>
	    <area alt="" title="" href="#" shape="rect" coords="982,485,1000,499" id="realpivot-hsbar2" class="realpivot-sbar-button realpivot-sbar-hfbutton"/>
	    <area alt="" title="" href="#" shape="rect" coords="24,486,361,499" id="realpivot-hsbar3" class="realpivot-sbar-thumb"/>

	    <area alt="" title="" href="#" shape="rect" coords="1001,4,1015,22" id="realpivot-vsbar1" class="realpivot-sbar-button realpivot-sbar-vnbutton"/>
	    <area alt="" title="" href="#" shape="rect" coords="1001,467,1014,482" id="realpivot-vsbar2" class="realpivot-sbar-button realpivot-sbar-vfbutton"/>
	    <area alt="" title="" href="#" shape="rect" coords="1001,25,1015,101" id="realpivot-vsbar3" class="realpivot-sbar-thumb"/>

	    <area alt="" title="" href="#" shape="rect" coords="1001,484,1015,499" id="realpivot-sbar-corner" class="realpivot-sbar-corner"/>

	    <area alt="" title="" href="#" shape="rect" coords="4,486,999,500" id="realpivot-hsbar" class="realpivot-sbar"/>
	    <area alt="" title="" href="#" shape="rect" coords="1001,3,1016,484" id="realpivot-vsbar" class="realpivot-sbar"/>

	</map>
</div>

<div id="eventLog" style="width:100%; height:50px; border: 0px solid #5d8cc9; 
text-align:center;
font-size: 2.0em;
line-height: 1.0em"
>
<center></center>
</div>

<!-- setup -->

<div id="setupContainer" style="width:1021px; height:503px;">
	<img class="setupBox" src="/resource/image/pivot_images/pivot_setupImagemap.png" id="imagemap2" alt="" usemap="#Map" width="1021px" height="503px"/>
	<map name="Map" id="Map">
		
		<area alt="" title="" href="#" shape="rect" coords="191,30,830,86" id="realpivot-setup-head" class="realpivot-setup-head"/>

		<area alt="" title="" href="#" shape="rect" coords="211,106,229,125" id="realpivot-setup-section-title-field" class="realpivot-setup-section-title-field"/>
		<area alt="" title="" href="#" shape="rect" coords="231,106,286,123" id="realpivot-setup-section-title1" class="realpivot-setup-section-title"/>
		<area alt="" title="" href="#" shape="rect" coords="211,105,347,125" id="realpivot-setup-section-title2" class="realpivot-setup-section-title"/>

		<area alt="" title="" href="#" shape="rect" coords="358,106,377,123" id="realpivot-setup-section-title-column" class="realpivot-setup-section-title-column"/>
		<area alt="" title="" href="#" shape="rect" coords="377,107,433,123" id="realpivot-setup-section-title3" class="realpivot-setup-section-title"/>
		<area alt="" title="" href="#" shape="rect" coords="357,106,579,124" id="realpivot-setup-section-title4" class="realpivot-setup-section-title"/>

		<area alt="" title="" href="#" shape="rect" coords="588,107,607,123" id="realpivot-setup-section-title-row1" class="realpivot-setup-section-title-row"/>
		<area alt="" title="" href="#" shape="rect" coords="608,107,654,124" id="realpivot-setup-section-title-row2" class="realpivot-setup-section-title"/>
		<area alt="" title="" href="#" shape="rect" coords="588,106,810,124" id="realpivot-setup-section-title5" class="realpivot-setup-section-title"/>

		<area alt="" title="" href="#" shape="rect" coords="212,129,331,154" id="realpivot-setup-field1" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="212,157,331,184" id="realpivot-setup-field2" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="212,184,331,211" id="realpivot-setup-field3" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="212,213,331,240" id="realpivot-setup-field4" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="212,242,331,267" id="realpivot-setup-field5" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="212,269,331,295" id="realpivot-setup-field6" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="212,298,331,322" id="realpivot-setup-field7" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="212,326,331,351" id="realpivot-setup-field8" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="212,353,331,379" id="realpivot-setup-field9" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="209,127,347,378" id="realpivot-setup-section-merged" class="realpivot-setup-section-merged"/>
		<area alt="" title="" href="#" shape="rect" coords="209,106,349,393" id="realpivot-setup-cell-all" class="realpivot-setup-cell realpivot-setup-cell-all"/>

		<!-- 컬럼, 행 필드-->
		<area alt="" title="" href="#" shape="rect" coords="545,130,561,152" id="realpivot-setup-field-sort-asc1" class="realpivot-setup-field-sort-asc"/>
		<area alt="" title="" href="#" shape="rect" coords="545,157,561,183" id="realpivot-setup-field-sort-asc2" class="realpivot-setup-field-sort-asc"/>

		<area alt="" title="" href="#" shape="rect" coords="563,131,576,153" id="realpivot-setup-field-remove1" class="realpivot-setup-field-remove"/>
		<area alt="" title="" href="#" shape="rect" coords="563,157,576,183" id="realpivot-setup-field-remove2" class="realpivot-setup-field-remove"/>

		<area alt="" title="" href="#" shape="rect" coords="776,130,792,152" id="realpivot-setup-field-sort-asc3" class="realpivot-setup-field-sort-asc"/>
		<area alt="" title="" href="#" shape="rect" coords="776,159,792,181" id="realpivot-setup-field-sort-desc" class="realpivot-setup-field-sort-desc"/>

		<area alt="" title="" href="#" shape="rect" coords="794,131,806,154" id="realpivot-setup-field-remove3" class="realpivot-setup-field-remove"/>
		<area alt="" title="" href="#" shape="rect" coords="794,160,806,182" id="realpivot-setup-field-remove4" class="realpivot-setup-field-remove"/>

		<!-- 값 필드 -->
		<area alt="" title="" href="#" shape="rect" coords="490,277,532,296" id="realpivot-setup-field-value1" class="realpivot-setup realpivot-setup-field-value"/>
		<area alt="" title="" href="#" shape="rect" coords="490,306,532,327" id="realpivot-setup-field-value2" class="realpivot-setup realpivot-setup-field-value"/>
		<area alt="" title="" href="#" shape="rect" coords="537,278,562,298" id="realpivot-setup-field-value3" class="realpivot-setup btn-default btn-small realpivot-setup-field-value"/>
		<area alt="" title="" href="#" shape="rect" coords="536,307,561,328" id="realpivot-setup-field-value4" class="realpivot-setup btn-default btn-small realpivot-setup-field-value"/>
		<area alt="" title="" href="#" shape="rect" coords="563,279,576,296" id="realpivot-setup-field-remove5" class="realpivot-setup-field-remove"/>
		<area alt="" title="" href="#" shape="rect" coords="563,306,576,326" id="realpivot-setup-field-remove6" class="realpivot-setup-field-remove"/>

		<area alt="" title="" href="#" shape="rect" coords="362,131,575,154" id="realpivot-setup-field10" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="360,159,576,184" id="realpivot-setup-field11" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="592,131,806,154" id="realpivot-setup-field12" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="592,158,806,182" id="realpivot-setup-field13" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="361,276,576,300" id="realpivot-setup-field14" class="realpivot-setup-field"/>
		<area alt="" title="" href="#" shape="rect" coords="361,303,576,329" id="realpivot-setup-field15" class="realpivot-setup-field"/>

		<area alt="" title="" href="#" shape="rect" coords="358,254,376,270" id="realpivot-setup-section-title-value" class="realpivot-setup-section-title-value"/>
		<area alt="" title="" href="#" shape="rect" coords="377,253,420,270" id="realpivot-setup-section-title6" class="realpivot-setup-section-title"/>
		<area alt="" title="" href="#" shape="rect" coords="590,251,605,270" id="realpivot-setup-section-title-filter" class="realpivot-setup-section-title-filter"/>
		<area alt="" title="" href="#" shape="rect" coords="607,251,664,270" id="realpivot-setup-section-title7" class="realpivot-setup-section-title"/>
		<area alt="" title="" href="#" shape="rect" coords="761,246,811,270" id="realpivot-setup-field-filter" class="realpivot-setup realpivot-setup-field-filter"/>

		<area alt="" title="" href="#" shape="rect" coords="358,247,578,270" id="realpivot-setup-section-title8" class="realpivot-setup-section-title"/>
		<area alt="" title="" href="#" shape="rect" coords="590,247,811,270" id="realpivot-setup-section-title9" class="realpivot-setup-section-title"/>

		<area alt="" title="" href="#" shape="rect" coords="358,126,578,233" id="realpivot-setup-section1" class="realpivot-setup-section"/>
		<area alt="" title="" href="#" shape="rect" coords="588,126,809,231" id="realpivot-setup-section2" class="realpivot-setup-section"/>
		<area alt="" title="" href="#" shape="rect" coords="357,271,578,378" id="realpivot-setup-section3" class="realpivot-setup-section"/>
		<area alt="" title="" href="#" shape="rect" coords="588,271,810,379" id="realpivot-setup-section4" class="realpivot-setup-section"/>

		<area alt="" title="" href="#" shape="rect" coords="357,106,580,393" id="realpivot-setup-cell-normal1" class="realpivot-setup-cell realpivot-setup-cell-normal"/>
		<area alt="" title="" href="#" shape="rect" coords="587,106,811,393" id="realpivot-setup-cell-normal2" class="realpivot-setup-cell realpivot-setup-cell-normal"/>

		<!-- 적용, 취소 -->
		<area alt="" title="" href="#" shape="rect" coords="460,424,508,457" id="realpivot-setup-set" class="btn-primary realpivot-setup"/>
		<area alt="" title="" href="#" shape="rect" coords="512,424,559,457" id="realpivot-setup-cancel" class="btn-primary realpivot-setup"/>
		<area alt="" title="" href="#" shape="rect" coords="191,408,829,472" id="realpivot-setup-foot" class="realpivot-setup-foot"/>

		<area alt="" title="" href="#" shape="rect" coords="189,28,831,474" id="realpivot-setup" class="realpivot-setup"/>
	</map>
</div>

<div id="setupEventLog" style="width:100%; height:50px; border: 0px solid #5d8cc9; 
text-align:center;
font-size: 2.0em;
line-height: 1.0em"
>

<script>
$("#contextMenu").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#pivotSetup").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#pivotTitle").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#tooltip").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#progress").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#progressBar").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#progressMessage").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowHeaderSort1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowHeaderSort2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowHeaderText").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowHeader").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#valueHeaderText").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#valueHeader").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colHeaderSort1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colHeaderSort2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colHeaderText").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colHeader").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colExpander-expand1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colExpander-expand2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colLabelGroup1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colLabelGroup2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colSumTotal").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colSum1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colSum2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colSum3").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colSum4").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colLabel2-1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#colLabel3-1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySumTotal1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySumTotal2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySum1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySum2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySum3").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySum4").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#bodySum5").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#bodyValue1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#bodyValue2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowSumTotal").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowSumLevel1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowSumLevel2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowExpander-expand1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowExpander-expand2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowExpander-collapse").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowLabelGroup").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowLabelLevel1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#rowLabelLevel2").mouseover( function(event){
	classLog(event.currentTarget.className)
});

$("#realpivot-hsbar1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#realpivot-hsbar2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#realpivot-hsbar3").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#realpivot-vsbar1").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#realpivot-vsbar2").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#realpivot-vsbar3").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#realpivot-sbar-corner").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#realpivot-hsbar").mouseover( function(event){
	classLog(event.currentTarget.className)
});
$("#realpivot-vsbar").mouseover( function(event){
	classLog(event.currentTarget.className)
});

function classLog(className){
	document.getElementById("eventLog").innerHTML = className
};

/* setup */
$("#realpivot-setup").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-head").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title1").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title2").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title3").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title4").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title5").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title6").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title7").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title8").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title9").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title-field").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title-column").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title-row1").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title-row2").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});

$("#realpivot-setup-field1").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field2").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field3").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field4").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field5").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field6").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field7").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field8").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field9").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-merged").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-cell-all").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});

$("#realpivot-setup-field10").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field11").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field12").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field13").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-cell-normal1").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});

$("#realpivot-setup-field14").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field15").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-cell-normal2").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});

$("#realpivot-setup-field-sort-asc1").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-sort-asc2").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-sort-asc3").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-sort-desc").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-remove1").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-remove2").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-remove3").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-remove4").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-remove5").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-remove6").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-value1").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-value2").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-value3").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-value4").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});

$("#realpivot-setup-section-title-value").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-value4").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section-title-filter").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-value4").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-field-filter").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});

$("#realpivot-setup-section1").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section2").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section3").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-section4").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});

$("#realpivot-setup-set").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});
$("#realpivot-setup-cancel").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});

$("#realpivot-setup-foot").mouseover( function(event){
	setupClassLog(event.currentTarget.className)
});

function setupClassLog(className){
	document.getElementById("setupEventLog").innerHTML = className
};


</script>