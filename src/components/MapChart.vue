<template>
  <div id="chartdiv">
  </div>
</template>

<script>
  import * as am4core from "@amcharts/amcharts4/core";
  import * as am4maps from "@amcharts/amcharts4/maps";
  import am4geodata_worldLow from "@amcharts/amcharts4-geodata/worldLow";
  import am4themes_animated from "@amcharts/amcharts4/themes/animated";

  am4core.useTheme(am4themes_animated);

  export default {
    name: 'MapChart',
    mounted() {
      // Create map instance
      var chart = am4core.create("chartdiv", am4maps.MapChart);
      chart.seriesContainer.draggable = false;
      chart.seriesContainer.resizable = false;
      chart.maxZoomLevel = 1.5;

      // Set map definition
      chart.geodata = am4geodata_worldLow;

      // Set projection
      chart.projection = new am4maps.projections.Miller();

      // Create map polygon series
      var polygonSeries = chart.series.push(new am4maps.MapPolygonSeries());

      // Make map load polygon (like country names) data from GeoJSON
      polygonSeries.useGeodata = true;

      // Configure series
      var polygonTemplate = polygonSeries.mapPolygons.template;
      polygonTemplate.tooltipText = "{name}";
      polygonTemplate.fill = am4core.color("#fff");
      polygonTemplate.stroke = am4core.color("#46c3cd")

      // Create hover state and set alternative fill color
      var hs = polygonTemplate.states.create("hover");
      hs.properties.fill = am4core.color("#000");

      // Remove Antarctica
      polygonSeries.exclude = ["AQ"];

      // Add some data
//      polygonSeries.data = [{
//        "id": "US",
//        "name": "United States",
//        "value": 100,
//        "fill": am4core.color("#F05C5C")
//      }, {
//        "id": "FR",
//        "name": "France",
//        "value": 50,
//        "fill": am4core.color("#5C5CFF")
//      }];

      // Bind "fill" property to "fill" key in data
      polygonTemplate.propertyFields.fill = "fill";
    }
  }

</script>

<style lang="scss" scoped>
  @import "../assets/scss/chart.scss"
</style>
