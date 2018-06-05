---
layout: page
title: 자동 필터링(Auto Filter)
order: 13
devbox: true
devboxfile: AutoFilter-devbox.md
published: true
categories:
  - 컬럼
tags: ['Filtering', '필터링', '필터', 'Custom', '자동', 'auto']
---

<link rel="stylesheet" href="/lib/css/jquery-ui-1.12.1.css">
<script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
<script>
var chkID;
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}

var onDoneDataSet = function() {
	gridView.setColumnProperty("CustomerID","header",{styles:{background:"linear,#22ffd500,#ffffd500,90"}})
	//사용자 필터 이벤트
	gridView.onFilterActionClicked = function (grid, column, action, x, y) {
	  
	  if (action == "CustomFilter") {
	    var offset = $("#realgrid").offset();

	    showAutoFiltering(column, x + offset.left - 260, y + offset.top);
	  }
	  setTimeout(function(){
	    document.getElementById("customerText").focus();
	  }, 100)

	};

	$(".btn.small").css("padding", ".25rem 1.16rem")

	//자동완성
	var autocomplete_text = dataProvider.getDistinctValues("CustomerID");

	$("#customerText").autocomplete({
		source: autocomplete_text
	});

	//자동 필터 목록 생성
	var customerText = dataProvider.getDistinctValues("CustomerID");
	for(var i = 0; i < customerText.length; i++){
		var span = $("#spanFilters");
		var label = $("<label />").appendTo(span);
		$("<input />", { type: "checkbox", id: customerText[i], name: "chkAutoFilterItem", value: customerText[i], checked: false}).appendTo(label);
		label.append(customerText[i]);
		span.append("<br/>");
		document.getElementById("customerText").value = ""
	}
	
}

function showAutoFiltering(column, x, y) {
    $("#divAutoFilter").css("left", x);
    $("#divAutoFilter").css("top", y);
 
    $("#divAutoFilter").show();
}

function setCustomFilter(){
	var elementText = document.getElementById($("#customerText").val());
	if(elementText){
		elementText.checked = true
		applyAutoFilter();
		document.getElementById("customerText").value = ""
	} else if ($("#customerText").val() == ""){
		alert("필터로 검색할 값을 입력하세요.")
	}else{
		var span = $("#spanFilters");
		var label = $("<label />").appendTo(span);
		$("<input />", { type: "checkbox", id: $("#customerText").val(), name: "chkAutoFilterItem", value: $("#customerText").val(), checked: true}).appendTo(label);
		label.append($("#customerText").val());
		span.append("<br/>");
		document.getElementById("customerText").value = ""
		applyAutoFilter();
	}
}

function applyAutoFilter() {
	var filterExpr = "";
	var filterItems = $('input[name="chkAutoFilterItem"]:checked');
	autoFilterItems = [];
	for (var i = 0; i < filterItems.length; i++) {
		autoFilterItems.push(filterItems[i].value);
		if (filterExpr != "")
		filterExpr += " or ";
		filterExpr += "(value like '%" + filterItems[i].value + "%')";
	};

	var filters = {
		name: "auto_result",
		criteria: filterExpr,
		active: true,
		hidden:true
	};

	gridView.addColumnFilters("CustomerID", filters, true);
	$("#divAutoFilter").hide();
	var chkArr = [];
	$("input[name=chkAutoFilterItem]:checked").each(function() {
		chkArr.push($(this).val());
	});
	chkID = chkArr;
};

function closeAutoFilter() {
	$("#divAutoFilter").hide();
	$("input[name=chkAutoFilterItem]:checkbox").each(function() {
		$(this).attr("checked", false);
	});
	if(chkID !== undefined){
		for(var i = 0; i < chkID.length; i++){
			document.getElementById(chkID[i]).checked = true
		}
	}
}

</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="DefaultColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}


<div id="divAutoFilter" style="display:none; position:absolute; height:280px; width:149px; background-color:#eeeeee; border:1px solid black;">
	<input type="text" id="customerText" placeholder="Custom Filter" style="height:20px;width:146px" onkeypress="if(event.keyCode==13) {setCustomFilter();}" autofocus>
    <span id="spanFilters" style="overflow-y:scroll; display:block; width:100%; height:230px"></span>

    <a class="btn secondary small lowercase" onclick="applyAutoFilter();" id="applyAutoFilter">Apply</a>&nbsp;
    <a class="btn secondary small lowercase" onclick="closeAutoFilter();" id="cancelAutoFilter">Cancel</a>
</div>
