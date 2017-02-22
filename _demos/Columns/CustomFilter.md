---
layout: page
title: 사용자 필터링(Custom Filter)
order: 11
devbox: true
devboxfile: CustomFilter-devbox.md
categories:
  - 컬럼
tags: ['Filtering', '필터링', '필터', 'Custom']
---

<script>
var chkID;
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}

var onDoneDataSet = function() {
	//사용자 필터 이벤트
	gridView.onFilterActionClicked = function (grid, column, action, x, y) {
	  
	  console.log("onFilterActionClicked");
	  if (action == "CustomFilter") {
	    var offset = $("#realgrid").offset();

	    showAutoFiltering(column, x + offset.left - 260, y + offset.top);
	  }
	  setTimeout(function(){
	    document.getElementById("customerText").focus();
	  }, 100)

	};
}

function showAutoFiltering(column, x, y) {
    $("#divAutoFilter").css("left", x);
    $("#divAutoFilter").css("top", y);
 
    $("#divAutoFilter").show();
}

function setCustomFilter(){
	if(document.getElementById($("#customerText").val())){
		alert("이미 해당 필터 조건이 존재합니다.")
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
  console.log(filterExpr);
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
  for(var i = 0; i < chkID.length; i++){
  	document.getElementById(chkID[i]).checked = true
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


<div id="divAutoFilter" style="display:none; position:absolute; height:280px; width:146px; background-color:#eeeeee; border:1px solid black;">
	<input type="text" id="customerText" placeholder="Custom Filter" style="height:20px;width:144px" onkeypress="if(event.keyCode==13) {setCustomFilter();}" autofocus>
    <span id="spanFilters" style="overflow-y:scroll; display:block; width:100%; height:230px"></span>

    <a class="btn secondary small lowercase" onclick="applyAutoFilter();" id="applyAutoFilter">Apply</a>
    <a class="btn secondary small lowercase" onclick="closeAutoFilter();" id="cancelAutoFilter">Cancel</a>

</div>
