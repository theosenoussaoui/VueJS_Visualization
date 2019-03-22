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
  import { objectCountries } from "../assets/js/objectCountries.js";

  am4core.useTheme(am4themes_animated);

  export default {
    name: 'MapChart',
    mounted()
    {
      const secretKey = '474d3500db4940e2945a33eb7788710d';
      const objectCategories = [
        {
            id:     "w",
            name:   "International"
        },
        {
            id:     "n",
            name:   "National"
        },
        {
            id:     "b",
            name:   "Économie"
        },
        {
            id:     "t",
            name:   "Science / Tech"
        },
        {
            id:     "e",
            name:   "Divertissement"
        },
        {
            id:     "s",
            name:   "Sports"
        },
        {
            id:     "m",
            name:   "Santé"
        },
        {
            id:     "_",
            name:   "À la une"
        }
      ];

      // Create map instance
      var chart = am4core.create("chartdiv", am4maps.MapChart);

      // Options
      chart.language.locale = am4lang_fr_FR;
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
      hs.properties.fill = am4core.color("#19BABA");

      // Remove Antarctica
      polygonSeries.exclude = ["AQ"];

      //zoom pays
      var lastSelected;

      polygonTemplate.events.on("hit", async function(event)
      {
        if (lastSelected)
        {
          lastSelected.isActive = false;
        }

        event.target.series.chart.zoomToMapObject(event.target);

        if (lastSelected !== event.target)
        {
          lastSelected = event.target;
          const countryName = event.target.dataItem.dataContext.name;

          if (objectCountries.hasOwnProperty(countryName))
          {
            console.log(objectCountries[countryName]);
            try
            {
                const countryCode = objectCountries[countryName]['id'];
                const url = "https://api.ozae.com/gnw/articles?date=20180701__20180702&edition=" + countryCode + "&key=" + secretKey + "&hard_limit=50";
                const response = await fetch(url);

                if (response.ok)
                {
                    let data = await response.json();
                    // const fragment = document.createDocumentFragment();
                    // for (let i = 0; i < data['articles'].length; i++)
                    // {
                    //     const div = document.createElement('div');
                    //     div.innerHTML = data['articles'][i]['name'];
                    //     fragment.appendChild(div);
                    // }
                    // document.getElementById('containerFetch').appendChild(fragment);
                    UIkit.modal.alert('UIkit alert!');
                    console.log(data);
                }
                else
                {
                    console.error('Retour du serveur : ', response.status);
                    // const div = document.createElement('div');
                    // div.innerHTML = "Retour du serveur : " + response.status;
                    // document.getElementById('containerFetch').appendChild(div);
                }
            }
            catch (error)
            {
                console.log(error);
                // const div = document.createElement('div');
                // div.innerHTML = error;
                // document.getElementById('containerFetch').appendChild(div);
            }

          }
          else
          {
            console.log('Données inexistantes pour ce pays');
          }
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

</script>

<style lang="scss" scoped>
  @import "../assets/scss/chart.scss"

</style>

<style lang="css" scoped>
  #chartdiv svg {
    filter: drop-shadow(3px 3px 0px rgba(25, 186, 186, 1))
  }

</style>