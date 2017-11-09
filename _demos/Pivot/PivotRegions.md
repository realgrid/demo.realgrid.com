---
layout: page
title: 피벗 영역
order: 8
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'Regions']
---

상세 영역 보기는 아래의 탭을 클릭하거나 최상위 요소탭 pivot 화면의 영역을 선택하면 해당 영역에 대한 상세 정보를 볼 수 있습니다.

<style type="text/css">
#container {
	width:936px;
	text-align:center;
}
.tab {
	list-style: none;
	margin: 0;
	padding: 0;
	overflow: hidden;
}
.tab li {
	float: left;
}
.tab li a {
	display: inline-block;
	border: 1px solid;
	border-color: #5d5d5d;
	color: #000;
	text-align: center;
	text-decoration: none;
	padding: 14px 8px;
	font-size: 15px;
	transition:0.3s;
}
.tabcontent {
	display: none;
	background-color:rgb(255,255,255);
	padding: 0px 0px;
	color:#fff;
}
ul.tab li.current{
	background-color: rgb(255,255,255);
	color: #fff;
}
.tabcontent.current {
	display: block;
}
</style>

<script src="/lib/jquery/jquery-1.11.2.min.js"></script>



<div id="container">
	<ul class="tab">
		<li class="current" data-tab="tab1"><a href="#">최상위 요소(div.rp)</a></li>
		<li data-tab="tab2"><a href="#">header</a></li>
		<li data-tab="tab3"><a href="#">column상위 요소(div.rp-col)</a></li>
		<li data-tab="tab4"><a href="#">row상위 요소(div.rp-row)</a></li>
		<li data-tab="tab5"><a href="#">body상위 요소(div.rp-body)</a></li>
	</ul>
	<div id="tab1" class="tabcontent current" style="border: 1px solid #000000; height: auto; padding:10px;">
		<img src="/resource/image/pivot_images/RealPivot.png" usemap="#view" width="944px" height="517px">

		<map name="view"> 
		  <area shape="rect" coords="1, 12, 137, 86" onclick="imageMap('tab2',1)" title="header 상세보기"/>
		  <area shape="rect" coords="130, 11, 920, 28" onclick="imageMap('tab2',1)" title="header 상세보기"/>
		  <area shape="rect" coords="139, 34, 921, 88" onclick="imageMap('tab3',2)" title="column 상세보기"/>
		  <area shape="rect" coords="20, 88, 139, 493" onclick="imageMap('tab4',3)" title="row 상세보기"/>
		  <area shape="rect" coords="140, 89, 939, 493" onclick="imageMap('tab5',4)" title="body 상세보기"/>
		</map>
	</div>

	<div id="tab2" class="tabcontent" style="border: 1px solid #000000; height: auto; padding:10px;">
		<img src="/resource/image/pivot_images/RealPivot_header_class.png">
	</div>
	<div id="tab3" class="tabcontent" style="border: 1px solid #000000; height: auto; padding:10px;">
		<img src="/resource/image/pivot_images/RealPivot_column_class.png">
	</div>
	<div id="tab4" class="tabcontent" style="border: 1px solid #000000; height: auto; padding:10px;">
		<img src="/resource/image/pivot_images/RealPivot_row_class.png">
	</div>
	<div id="tab5" class="tabcontent" style="border: 1px solid #000000; height: auto; padding:10px;">
		<img src="/resource/image/pivot_images/RealPivot_summary_class.png">
		<img src="/resource/image/pivot_images/RealPivot_value_class.png">
	</div>
</div>
<script>
	$(function() {
		$('ul.tab li').click(function() {
			var activeTab = $(this).attr('data-tab');
			console.log(this)
			$('ul.tab li').removeClass('current');
			$('.tabcontent').removeClass('current');
			$(this).addClass('current');
			$('#' + activeTab).addClass('current');
		})
	});
	function imageMap(dataTab, num){
		var activeTab = dataTab
		console.log(activeTab)
			$('ul.tab li').removeClass('current');
			$('.tabcontent').removeClass('current');
			$('ul.tab li')[num].setAttribute( 'class', 'current' )
			$('#' + activeTab).addClass('current');
	}
</script>