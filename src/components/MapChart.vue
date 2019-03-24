<template>
  <div id="chartdiv"></div>
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
  name: "MapChart",
  mounted() {
    const objectCategories = [
      {
        id: "w",
        name: "International"
      },
      {
        id: "n",
        name: "National"
      },
      {
        id: "b",
        name: "Économie"
      },
      {
        id: "t",
        name: "Science / Tech"
      },
      {
        id: "e",
        name: "Divertissement"
      },
      {
        id: "s",
        name: "Sports"
      },
      {
        id: "m",
        name: "Santé"
      },
      {
        id: "_",
        name: "À la une"
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
    polygonTemplate.stroke = am4core.color("#80D4BD");

    // Create hover state and set alternative fill color
    var hs = polygonTemplate.states.create("hover");
    hs.properties.fill = am4core.color("#19BABA");

    // Remove Antarctica
    polygonSeries.exclude = ["AQ"];

    //zoom pays
    var lastSelected;

    polygonTemplate.events.on("hit", async function(event) {
      if (lastSelected) {
        lastSelected.isActive = false;
      }

      event.target.series.chart.zoomToMapObject(event.target);

      if (lastSelected !== event.target) {
        lastSelected = event.target;
        const countryName = event.target.dataItem.dataContext.name;

        if (objectCountries.hasOwnProperty(countryName)) {
          console.log(objectCountries[countryName]);
          const countryCode = objectCountries[countryName]["id"];
          const countryNameFr = objectCountries[countryName]["nameFr"];

          let [
            articlesInternational,
            articlesNational,
            articlesEconomie,
            articlesScienceTech,
            articlesDivertissement,
            articlesSports,
            articlesSante,
            articlesUne
          ] = await Promise.all([
            getArticles(countryCode, "w"),
            getArticles(countryCode, "n"),
            getArticles(countryCode, "b"),
            getArticles(countryCode, "t"),
            getArticles(countryCode, "e"),
            getArticles(countryCode, "s"),
            getArticles(countryCode, "m"),
            getArticles(countryCode, "_")
          ]);

          console.log("ok");

          console.log(articlesInternational);
          console.log(articlesNational);
          console.log(articlesEconomie);
          console.log(articlesScienceTech);
          console.log(articlesDivertissement);
          console.log(articlesSports);
          console.log(articlesSante);
          console.log(articlesUne);

          displayPopup(
            countryNameFr,
            articlesInternational,
            articlesNational,
            articlesEconomie,
            articlesScienceTech,
            articlesDivertissement,
            articlesSports,
            articlesSante,
            articlesUne
          );
        } else {
          console.log("Données inexistantes pour ce pays");
        }
      }
      //réinitialisation du zoom lors d'un clic sur un pays actif
      else {
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
    button.icon.path =
      "M16,8 L14,8 L14,16 L10,16 L10,10 L6,10 L6,16 L2,16 L2,8 L0,8 L8,0 L16,8 Z M16,8";

    // Bind "fill" property to "fill" key in data
    polygonTemplate.propertyFields.fill = "fill";

    async function getArticles(countryCode, topic) {
      try {
        const secretKey = "474d3500db4940e2945a33eb7788710d";
        const date = new Date();

        //date du jour
        const day =
          date.getDate().toString().length == 1
            ? "0" + date.getDate()
            : date.getDate();
        const month =
          (date.getMonth() + 1).toString().length == 1
            ? "0" + (date.getMonth() + 1)
            : date.getMonth() + 1;
        const year = date.getFullYear();
        const currentDateDMY = year + month + day;
        const currentDate = new Date(year + "/" + month + "/" + day);

        //date d'il y a un mois
        let beforeDate = new Date(currentDate.getTime());
        beforeDate = new Date(beforeDate.setMonth(beforeDate.getMonth() - 1));
        const dayBefore =
          beforeDate.getDate().toString().length == 1
            ? "0" + beforeDate.getDate()
            : beforeDate.getDate();
        const monthBefore =
          (beforeDate.getMonth() + 1).toString().length == 1
            ? "0" + (beforeDate.getMonth() + 1)
            : beforeDate.getMonth() + 1;
        const yearBefore = beforeDate.getFullYear();
        const beforeDateDMY = yearBefore + monthBefore + dayBefore;

        const url =
          "https://api.ozae.com/gnw/articles?date=" +
          beforeDateDMY +
          "__" +
          currentDateDMY +
          "&edition=" +
          countryCode +
          "&key=" +
          secretKey +
          "&hard_limit=10" +
          "&topic=" +
          topic;

        const response = await fetch(url);

        if (response.ok) {
          let data = await response.json();
          // const fragment = document.createDocumentFragment();
          // for (let i = 0; i < data['articles'].length; i++)
          // {
          //     const div = document.createElement('div');
          //     div.innerHTML = data['articles'][i]['name'];
          //     fragment.appendChild(div);
          // }
          // document.getElementById('containerFetch').appendChild(fragment);
          // UIkit.modal.alert('UIkit alert!');
          // console.log(data);
          return data;
        } else {
          console.error("Retour du serveur : ", response.status);
          return response.status;
          // const div = document.createElement('div');
          // div.innerHTML = "Retour du serveur : " + response.status;
          // document.getElementById('containerFetch').appendChild(div);
        }
      } catch (error) {
        console.log(error);
        return error;
        // const div = document.createElement('div');
        // div.innerHTML = error;
        // document.getElementById('containerFetch').appendChild(div);
      }
    }

    function displayPopup(
      countryNameFr,
      articlesInternational,
      articlesNational,
      articlesEconomie,
      articlesScienceTech,
      articlesDivertissement,
      articlesSports,
      articlesSante,
      articlesUne
    ) {
      const modalContainer = document.createElement("div");
      modalContainer.id = "modal-container";
      modalContainer.setAttribute("uk-modal", "");
      modalContainer.classList.add("uk-modal-container");

      const containerPopup = document.createElement("div");
      containerPopup.classList.add(
        "uk-modal-dialog",
        "uk-modal-body",
        "uk-overflow-auto"
      );
      containerPopup.setAttribute("uk-overflow-auto", "");

      const h2 = document.createElement("h2");
      h2.classList.add("uk-modal-title");
      h2.innerHTML = countryNameFr;

      const popupContent = document.createElement("div");
      popupContent.classList.add("uk-text-center");

      //tabs
      const ulTabs = document.createElement("ul");
      ulTabs.classList.add("uk-child-width-expand");
      ulTabs.setAttribute("uk-tab", "");

      const liTabs1 = document.createElement("li");
      const liTabs1Button = document.createElement("button");
      liTabs1Button.classList.add(
        "uk-button",
        "uk-button-default",
        "uk-margin-small-right"
      );
      const imgTabs1 = document.createElement("img");
      imgTabs1.setAttribute("src", "img/vacances.jpg");
      imgTabs1.setAttribute("alt", "Vacances");
      liTabs1Button.appendChild(imgTabs1);
      liTabs1.appendChild(liTabs1Button);

      const liTabs2 = document.createElement("li");
      const liTabs2Button = document.createElement("button");
      liTabs2Button.classList.add(
        "uk-button",
        "uk-button-default",
        "uk-margin-small-right"
      );
      const imgTabs2 = document.createElement("img");
      imgTabs2.setAttribute("src", "img/education.jpg");
      imgTabs2.setAttribute("alt", "Éducation");
      liTabs2Button.appendChild(imgTabs2);
      liTabs2.appendChild(liTabs2Button);

      const liTabs3 = document.createElement("li");
      const liTabs3Button = document.createElement("button");
      liTabs3Button.classList.add(
        "uk-button",
        "uk-button-default",
        "uk-margin-small-right"
      );
      const imgTabs3 = document.createElement("img");
      imgTabs3.setAttribute("src", "img/business.jpg");
      imgTabs3.setAttribute("alt", "Business");
      liTabs3Button.appendChild(imgTabs3);
      liTabs3.appendChild(liTabs3Button);

      const liTabs4 = document.createElement("li");
      const liTabs4Button = document.createElement("button");
      liTabs4Button.classList.add(
        "uk-button",
        "uk-button-default",
        "uk-margin-small-right"
      );
      const imgTabs4 = document.createElement("img");
      imgTabs4.setAttribute("src", "img/news.jpg");
      imgTabs4.setAttribute("alt", "News");
      liTabs4Button.appendChild(imgTabs4);
      liTabs4.appendChild(liTabs4Button);

      ulTabs.appendChild(liTabs1);
      ulTabs.appendChild(liTabs2);
      ulTabs.appendChild(liTabs3);
      ulTabs.appendChild(liTabs4);

      //switcher
      const ulSwitcher = document.createElement("ul");
      ulSwitcher.classList.add("uk-switcher", "uk-margin");

      const liSwitcher = document.createElement("li");

      // const ulAccordion = document.createElement('ul');
      // ulAccordion.setAttribute('uk-accordion', '')
      // ulAccordion.classList.add('uk-accordion');

      // const liAccordion = document.createElement('li');

      // const liAccordionA = document.createElement('a');
      // liAccordionA.setAttribute('href', '#');
      // liAccordionA.classList.add('uk-accordion-title');
      // liAccordionA.innerHTML = "Catégorie";

      // const liAccordionDiv = document.createElement('div');
      // liAccordionDiv.setAttribute('hidden', '');
      // liAccordionDiv.setAttribute('aria-hidden', 'true');
      // liAccordionDiv.classList.add('uk-accordion-content');

      const categoryGrid = document.createElement("div");
      categoryGrid.setAttribute("uk-grid", "");
      categoryGrid.classList.add(
        "uk-child-width-1-3",
        "uk-grid-small",
        "uk-grid-match",
        "uk-grid"
      );

      for (var i = 0; i < 10; i++) {
        console.log(i);
        const gridElement = document.createElement("div");

        const gridCard = document.createElement("div");
        gridCard.classList.add("uk-card", "uk-card-default", "uk-margin-small");

        const gridCardHeader = document.createElement("div");
        gridCardHeader.classList.add("uk-card-header", "uk-text-truncate");

        const gridCardTitle = document.createElement("div");
        gridCardTitle.classList.add("uk-grid-small", "uk-flex-middle");
        gridCardTitle.setAttribute("uk-grid", "");

        const gridWidthExtends = document.createElement("div");
        gridWidthExtends.classList.add("uk-width-expands");

        const h3Title = document.createElement("h3");
        h3Title.classList.add("uk-card-title", "uk-margin-remove-bottom");
        h3Title.innerHTML = articlesDivertissement.articles[i].name;

        const gridCardBody = document.createElement("div");
        gridCardBody.classList.add("uk-card-body");

        const gridCardBodyP = document.createElement("p");

        gridCardBodyP.innerHTML = articlesDivertissement.articles[i].name;

        const gridCardFooter = document.createElement("div");
        gridCardFooter.classList.add("uk-card-footer");

        const gridCardFooterA = document.createElement("a");
        gridCardFooterA.setAttribute(
          "href",
          "" + articlesDivertissement.articles[i].url + ""
        );
        gridCardFooterA.setAttribute(
          "target","_blank");
        gridCardFooterA.classList.add("uk-button", "uk-button-text");
        gridCardFooterA.innerHTML = "Lire l'article";
        gridCardHeader.appendChild(gridCardTitle);
        gridCardBody.appendChild(gridCardBodyP);
        gridCardFooter.appendChild(gridCardFooterA);
        gridCard.appendChild(gridCardHeader);
        gridCardHeader.appendChild(gridCardTitle);
        gridCardTitle.appendChild(gridWidthExtends);
        gridWidthExtends.appendChild(h3Title);
        gridCard.appendChild(gridCardBody);
        gridCard.appendChild(gridCardFooter);
        gridElement.appendChild(gridCard);
        categoryGrid.appendChild(gridElement);
      }
      liSwitcher.appendChild(categoryGrid);
      // liAccordion.appendChild(liAccordionA);
      // liAccordion.appendChild(liAccordionDiv);
      // ulAccordion.appendChild(liAccordion);
      // liSwitcher.appendChild(ulAccordion);
      ulSwitcher.appendChild(liSwitcher);

      popupContent.appendChild(ulTabs);
      popupContent.appendChild(ulSwitcher);

      containerPopup.appendChild(h2);
      containerPopup.appendChild(popupContent);

      modalContainer.appendChild(containerPopup);

      const element = document.createElement("div");

      element.appendChild(modalContainer);

      console.log(element.innerHTML);
      UIkit.modal(element.innerHTML).show();
      // UIkit.modal.dialog(modalContainer.innerHTML);
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/chart.scss";
</style>

<style lang="css" scoped>
#chartdiv svg {
  filter: drop-shadow(3px 3px 0px rgba(25, 186, 186, 1));
}
</style>