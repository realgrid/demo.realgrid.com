---
layout: page
title: 기본 편집기
order: 6
devbox: true
devboxfile: Editors-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', '편집기', 'editor']
---

리얼그리드는 라인, 멀티라인, 드롭다운, 날짜, 검색 등의 다양한 형태의 편집기를 제공 하고 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
    var CustomerNames = ["ALFKI", "ANATR", "ANTON", "AROUT", "BERGS", "BLAUS", "BLONP", "BOLID", "BONAP", "BOTTM", "BSBEV", "CACTU", "CENTC", "CHOPS", "COMMI", "CONSH", "DRACD", "DUMON", "EASTC", "ERNSH", "FAMIA", "FISSA", "FOLIG", "FOLKO", "FRANK", "FRANR", "FRANS", "FURIB", "GALED", "GODOS", "GOURL", "GREAL", "GROSR", "HANAR", "HILAA", "HUNGC", "HUNGO", "ISLAT", "KOENE", "LACOR", "LAMAI", "LAUGB", "LAZYK", "LEHMS", "LETSS", "LILAS", "LINOD", "LONEP", "MAGAA", "MAISD", "MEREP", "MORGK", "NORTS", "OCEAN", "OLDWO", "OTTIK", "PARIS", "PERIC", "PICCO", "PRINI", "QUEDE", "QUEEN", "QUICK", "RANCH", "RATTC", "REGGC", "RICAR", "RICSU", "ROMEY", "SANTG", "SAVEA", "SEVES", "SIMOB", "SPECD", "SPLIR", "SUPRD", "THEBI", "THECR", "TOMSP", "TORTU", "TRADH", "TRAIH", "VAFFE", "VICTE", "VINET", "WANDK", "WARTH", "WELLI", "WHITC", "WILMK", "WOLZA"];

    gridView.onEditSearch = function (grid, index, text) {
        console.log("onEditSearch:" + index.itemIndex + "," + index.column + ", " + text);
        var items = CustomerNames.filter(function (str) {
            return str.indexOf(text) == 0;
        });
        grid.fillEditSearchItems(index.column, text, items);
    };

    gridView.setValue(0, "Quantity", 1200.12);
    gridView.setValue(1, "Quantity", 123433.144);
    gridView.setValue(2, "Quantity", 200.12);
    gridView.setValue(3, "Quantity", 423453.92);
    gridView.setValue(3, "Quantity", 150.0);
    gridView.setValue(3, "Quantity", 10.62);

  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="EditorField"
  columnSet="EditorColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_Editors"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}