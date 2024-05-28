---
layout: post
title: "Countries visited"
---

<html>
<head>
  <!-- Scripts for GeoCharts. Copied from https://developers.google.com/chart/interactive/docs/gallery/geochart -->
  <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
  <script type="text/javascript">
    google.charts.load('current', {'packages':['geochart']});
    google.charts.setOnLoadCallback(drawRegionsMap);
    
    function drawRegionsMap() {
      
      var data = google.visualization.arrayToDataTable([
        ['Country'],
        ['India'],
        ['United States'],
        ['Sri Lanka'],
        ['Singapore'],
        ['Malaysia'],
        ['Switzerland'],
        ['Mexico'],
        ['France'],
        ['Italy'],
        ['Spain'],
        ['Iceland'],
        ['Austria'],
        ['Germany'],
        ['Czech Republic'],
        ['Israel'],
        ['United Kingdom'],
        ['Turkey'],
        ['Maldives'],
        ['Portugal'],
      ]);
      
      var options = {
        defaultColor: 'blue',
        domain: 'IN'
      };
      
      var chart = new google.visualization.GeoChart(document.getElementById('regions_div'));
      
      chart.draw(data, options);
    }
  </script>
</head>
<body>
    <div id="regions_div" style="width: 100%;"></div>
</body>
</html>