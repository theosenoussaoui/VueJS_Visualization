<template>
  <div id="chartdiv">
  </div>
</template>

<script>
  import * as am4core from "@amcharts/amcharts4/core";
  import * as am4maps from "@amcharts/amcharts4/maps";
  import am4lang_fr_FR from "@amcharts/amcharts4/lang/fr_FR";
  import am4geodata_worldHigh from "@amcharts/amcharts4-geodata/worldHigh";
  import am4themes_animated from "@amcharts/amcharts4/themes/animated";

  am4core.useTheme(am4themes_animated);

  export default {
    name: 'MapChart',
    mounted() {
      // Create map instance
      var chart = am4core.create("chartdiv", am4maps.MapChart);

      // Options
      chart.language.locale = am4lang_fr_FR;
      console.log(am4lang_fr_FR);
      chart.seriesContainer.draggable = false;
      chart.seriesContainer.resizable = false;
      chart.maxZoomLevel = 5;
      chart.hideCredits = true;
      // Set map definition
      chart.geodata = am4geodata_worldHigh;

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
      polygonTemplate.stroke = am4core.color("#80D4BD")

      // Create hover state and set alternative fill color
      var hs = polygonTemplate.states.create("hover");
      hs.properties.fill = am4core.color("#A7DFB2");

      // Remove Antarctica
      polygonSeries.exclude = ["AQ"];

      //zoom pays
      var lastSelected;
      polygonTemplate.events.on("hit", async function(event)
      {
        if (lastSelected)
        {
          // This line serves multiple purposes:
          // 1. Clicking a country twice actually de-activates, the line below
          //    de-activates it in advance, so the toggle then re-activates, making it
          //    appear as if it was never de-activated to begin with.
          // 2. Previously activated countries should be de-activated.
          lastSelected.isActive = false;
        }
        event.target.series.chart.zoomToMapObject(event.target);
        if (lastSelected !== event.target)
        {
          lastSelected = event.target;
          console.log(event.target.dataItem.dataContext);
        }
        //réinitialisation du zoom lors d'un clic sur un pays actif
        else
        {
          chart.goHome();
          lastSelected = false;
        }
      });

      //bouton home
      let button = chart.chartContainer.createChild(am4core.Button);
      button.padding(5, 5, 5, 5);
      button.width = 26;
      button.fill = "#46C3CD";
      button.background.fill = "#FFFFFF";
      button.background.hoverOptions.fill = "#333333";
      button.align = "right";
      button.marginRight = 15;
      button.events.on("hit", function() {
        chart.goHome();
        lastSelected = false;
      });
      button.icon = new am4core.Sprite();
      button.icon.path = "M16,8 L14,8 L14,16 L10,16 L10,10 L6,10 L6,16 L2,16 L2,8 L0,8 L8,0 L16,8 Z M16,8";

      // Bind "fill" property to "fill" key in data
      polygonTemplate.propertyFields.fill = "fill";
    }
  }

  document.addEventListener('click', function(event)
  {
    if (event.target.matches('#chartdiv'))
    {
      alert('aeraezt');
    }
  });
  
  

</script>

<style lang="scss" scoped>
  @import "../assets/scss/chart.scss"
</style>
