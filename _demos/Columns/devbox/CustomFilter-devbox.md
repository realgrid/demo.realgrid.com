#### 사용자 필터링

Custom Filter버튼 클릭 시 `CustomerID` 컬럼에 `Custom Filter`가 설정되며
Custom Filter의 textBox에 `value` 값 입력 후 Enter키 입력 시 필터가 추가됩니다.  
해당 filter값을 체크 후 `Apply버튼`을 클릭하면 선택된 값으로 필터링 합니다.

<a class="btn primary small round lowercase" id="btnSetFilters">Custom Filter</a>


<script>
var oldFilterColumn;
$("#btnSetFilters").click(function() { 
	/*
	//var filterColumn = $("#selFilterColumn").val();
    //var filterOper = $("#selFilterOperator").val();
    //var filterValue;
    var filterColumn = "OrderID";
    var filterOper = "="
    var filterValue = "10248"

    if ($("#selFilterType").val() == "value") {
        filterValue = "'" + $("#txtFilterValue").val() + "'";
    } else {
        var targetField = grdMain.getColumnProperty($("#selCompareColumn").val(), "fieldName");
        filterValue = "values['" + targetField + "']";
    }

    var filters = {
        name: "custom_filter",
        criteria: "value " + filterOper + " " + filterValue,
        active: true
    };
 
    // 이전 customer filter를 제거
    if (oldFilterColumn)
    gridView.removeColumnFilters(oldFilterColumn, "custom_filter");
    gridView.addColumnFilters(filterColumn, filters, true);
 
    oldFilterColumn = filterColumn;
    */
    var actions = [{
	  name: "CustomFilter",
	  text: "CustomFilter",
	  description: "Custom Filter Actions"
	}];
	gridView.setColumnFilterActions('CustomerID', actions);

	//사용자 필터 이벤트
	gridView.onFilterActionClicked = function (grid, column, action, x, y) {
	  console.log("onFilterActionClicked");
	  if (action == "CustomFilter") {
	    var offset = $("#realgrid").offset();

	    showAutoFiltering(column, x + offset.left - 260, y + offset.top);
	  }
	};

	var autoFiltercolumn;
	var autoFilterItems = [];

	function showAutoFiltering(column, x, y) {
	    $("#divAutoFilter").css("left", x);
	    $("#divAutoFilter").css("top", y);
	 
	    $("#divAutoFilter").show();
	}
});
</script>