#### 행 높이를 변경가능하게 설정

```js
gridView.setDisplayOptions({
  heightMeasurer: "fixed",
  rowResizable: true,
  rowHeight: 80
});
```

#### fillHeight 설정하는 방법


```js
{
  "type": "group",
  "orientation": "vertical",
  "width": 120,
  "header": {
      "visible": false
  },
  "columns": [{
      "name": "OrderID",
      "fieldName": "OrderID",
      "width": "90",
      "fillHeight": 40,
      "styles": {
          "textAlignment": "center",
          "background": "#110000ff"
      },
      "header": {
          "text": "Order ID"
      }
  }, {
      "name": "CustomerID",
      "fieldName": "CustomerID",
      "width": "130",
      "styles": {
          "textAlignment": "center"
      },
      "header": {
          "text": "Customer ID"
      }
  }, {
      "name": "EmployeeID",
      "fieldName": "EmployeeID",
      "width": "100",
      "fillHeight": 60,
      "styles": {
          "textAlignment": "center",
          "background": "#1100ff00"
      },
      "header": {
          "text": "Employee ID"
      }
  }]
}
```


<script>


</script>

