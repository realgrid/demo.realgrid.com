---
layout: page
title: 데이터 필터링(Filtering)
order: 10
devbox: true
devboxfile: ColumnFiltering-devbox.md
published: true
categories:
  - 컬럼
tags: ['Filtering', '필터링', '필터']
---

그리드 [FilteringOptions](http://help.realgrid.com/api/types/FilteringOptions/){:target="_blank"}.enabled 가 true이고, 컬럼에 filter들이 설정되면 컬럼 헤더에 필터 핸들이 표시되고, 사용자는 그 핸들을 클릭해서 표시되는 필터 리스트를 이용 컬럼 별로 데이터를 필터링할 수 있습니다. 

한 컬럼 내에서 복수 필터가 선택되면 필터셋 중 하나의 필터 조건에만 해당되어도 행들이 표시됩니다. 하지만 여러 컬럼에 필터가 설정되면 모든 컬럼의 필터셋에 해당되는 행들만이 표시됩니다. 

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
	gridView.onFilterActionClicked = function (grid, column, action, x, y) {
	  if (action == "autoFilter") {
	   var offset = $("#realgrid").offset();

	   showAutoFiltering(column, x + offset.left - 260, y + offset.top);
	}
  };    


	var autoFiltercolumn;
	var autoFilterItems = [];

	function showAutoFiltering(column, x, y) {
	  autoFiltercolumn = column;
	  var fieldName = gridView.columnByName(column).fieldName;
	  var values = dataProvider.getDistinctValues(fieldName, 100);

	  var span = $("#spanFilters");
	  span.empty();
	  values.forEach(function (v) {
	    var label = $("<label />").appendTo(span);
	    var existsFilter = autoFilterItems.indexOf(v) >= 0;
	    $("<input />", { type: "checkbox", name: "chkAutoFilterItem", value: v, checked: existsFilter}).appendTo(label);
	    label.append(v);
	    span.append("<br/>");
	  });

	  $("#divAutoFilter").css("left", x);
	  $("#divAutoFilter").css("top", y);

	  $("#divAutoFilter").show();
	}

	$("#applyAutoFilter").click(function() { 
	  var filterExpr = "";
	  var filterItems = $('input[name="chkAutoFilterItem"]:checked');
	  autoFilterItems = [];
	  for (var i = 0; i < filterItems.length; i++) {
	    autoFilterItems.push(filterItems[i].value);
	    if (filterExpr != "")
	      filterExpr += " or ";
	    filterExpr += "(value = '" + filterItems[i].value + "')";
	  };
	  var filters = {
	    name: "auto_result",
	    criteria: filterExpr,
	    active: true,
	    hidden:true
	  };

	  gridView.addColumnFilters(autoFiltercolumn, filters, true);
	  $("#divAutoFilter").hide();
	});

	$("#cancelAutoFilter").click(function() { 
	  $("#divAutoFilter").hide();
	});
    
    gridView.onFilterActionClicked = function (grid, column, action, x, y) {
	  if (action == "autoFilter") {
	    var offset = $("#realgrid").offset();

	    showAutoFiltering(column, x-260 + offset.left, y + offset.top);
	  }
	};

	gridView.setFilteringOptions({
	    selector: {
	        maxWidth: 130,
	        maxHeight: 200
	    }
	});

	var column = gridView.columnByName('CustomerID');
if (column) {
    var filters = [{
        name: "VINET",
        criteria: "value = 'VINET'"
    }, {
        name: "VICTE",
        criteria: "value = 'VICTE'"
    }, {
        name: "HANAR",
        criteria: "value = 'HANAR'"
    }, {
        name: "'VICTE' or 'HANAR'",
        criteria: "(value = 'VICTE') or (value = 'HANAR')"
    }, {
        name: "HANAR: value > 'HANAR'",
        criteria: "value > 'HANAR'"
    }, {
        name: "SUPRD",
        criteria: "value = 'SUPRD'"
    }, {
        name: "SUPRD: value <> 'SUPRD'",
        criteria: "value <> 'SUPRD'"
    }, {
        name: "not equal CustomerID2",
        criteria: "value <> values['CustomerID2']" // CustomerID와 CustomerID2가 상이한 경우
    }, {
        name: "W: value like 'L%'",
        criteria: "value like 'L%'"
    }, {
        name: "W: value not like 'L%'",
        criteria: "value not like 'L%'"
    }, {
        name: "S: value like '%S'",
        criteria: "value like '%S'"
    }, {
        name: "S: value not like '%S'",
        criteria: "value not like '%S'"
    }, { 
        name: "TC: value match 'TC'",
        criteria: "value match 'TC'" // 문자열에 TC가 포함된 경우
    }, {
        name: "match '^RATTC$|^SUPRD$'",
        criteria: "value match '^RATTC$|^SUPRD$'" //RATTC, SUPRD 중 하나인 경우
    }, { 
        name: "TC: value not match 'TC'",
        criteria: "value not match 'TC'" // 문자열에 TC가 포함되지 않는 경우
    }];

    gridView.setColumnFilters('CustomerID', filters);

};

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

<div id="divAutoFilter" style="display:none; position:absolute; height:260px; width:146px; background-color:#eeeeee; border:1px solid black;">
    <span id="spanFilters" style="overflow-y:scroll; display:block; width:100%; height:230px">
    </span>
    <a class="btn secondary small lowercase" id="applyAutoFilter">Apply</a>
    <a class="btn secondary small lowercase" id="cancelAutoFilter">Cancel</a>

</div>
