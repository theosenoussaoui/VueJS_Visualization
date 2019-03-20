<template>
  <nav class="uk-navbar-container uk-navbar-transparent" uk-navbar>
    <div class="uk-navbar-left">
      <a href="" class="uk-logo"><img src="img/logo.png" alt="Logo Daily Map"></a>
      <ul class="uk-navbar-nav">
        <li><a href="#about" uk-toggle>À propos</a></li>
        <li><a href="#whoarewe" uk-toggle>Présentation</a></li>
        <li><a href="#faq" uk-toggle>FAQ</a></li>
      </ul>
    </div>
    <div id="about" class="uk-modal-full" uk-modal>
      <div class="uk-modal-dialog">
        <button class="uk-modal-close-full uk-close-large" type="button" uk-close></button>
        <div class="uk-grid-collapse uk-child-width-1-2@s uk-flex-middle" uk-grid>
          <div class="uk-padding-large">
            <img src="img/logo_couleur.png" alt="Logo Couleur Daily Map" width="200" />
            <h3>Daily Map est une plateforme interactive qui a pour but de rendre plus facilement accessible une information sur une destination en particulier.</h3>
            <h3>En effet, un internaute consulte au moins 8 sites avant se décider à réserver.</h3>
          </div>
          <div class="uk-background-contain" style="background-image: url('img/window.jpg');" uk-height-viewport></div>
        </div>
      </div>
    </div>

    <div id="whoarewe" class="uk-modal-full" uk-modal>
      <div class="uk-modal-dialog">
        <button class="uk-modal-close-full uk-close-large" type="button" uk-close></button>
        <div class="uk-grid-collapse uk-child-width-1-2@s uk-flex-middle" uk-grid>
          <div class="uk-padding-large">
            <img src="img/logo_couleur.png" alt="Logo Couleur Daily Map" width="200" />
            <h3>Daily Map permet de visualiser en direct des articles et informations pour un futur départ dans un pays étranger.</h3>
            <h3>À l’aide d’une carte interactive, vous pouvez sélectionner un pays, puis découvrir en fonction de la nature de votre recherche, des informations essentielles sur le pays. </h3>
            <h3>Vous souhaitez y aller pour le travail ? Les vacances ou bien pour vos études ? Notre site permet de répondre au mieux à vos questions en fonction de la catégorie sélectionnée.</h3>
            <h3>Alors n’hésitez pas à découvrir notre carte Daily Map !</h3>
          </div>
          <div class="uk-background-contain" style="background-image: url('img/window.jpg');" uk-height-viewport></div>
        </div>
      </div>
    </div>

    <div id="faq" class="uk-modal-full" uk-modal>
      <div class="uk-modal-dialog">
        <button class="uk-modal-close-full uk-close-large" type="button" uk-close></button>
        <div class="uk-grid-collapse uk-child-width-1-2@s uk-flex-middle" uk-grid>
          <div class="uk-padding-large">
            <ul uk-accordion>
              <li class="uk-open">
                <a class="uk-accordion-title" href="#">
                  <h3>Qu’est-ce-que Daily Map ?</h3>
                </a>
                <div class="uk-accordion-content">
                  <p><a href="#whoarewe" uk-toggle>Voir la page de présentation</a></p>
                </div>
              </li>
              <li>
                <a class="uk-accordion-title" href="#">
                  <h3>Toutes les informations sont-elles correctes ?</h3>
                </a>
                <div class="uk-accordion-content">
                  <p>Oui toutes les informations fournies sont correctes et analysées</p>
                </div>
              </li>
              <li>
                <a class="uk-accordion-title" href="#">
                  <h3>Comment fonctionne la carte ?</h3>
                </a>
                <div class="uk-accordion-content">
                  <p>La carte fonctionne comme un entonnoir, sélectionnez le pays, puis la raison de votre visite de ce pays, de là apparaîtront tous les articles touristiques en lien avec la nature de votre visite .</p>
                </div>
              </li>
<!--
              <li>
                <a class="uk-accordion-title" href="#">
                  <h3>Toutes les informations sont-elles correctes ?</h3>
                </a>
                <div class="uk-accordion-content">
                  <p>Oui toutes les informations fournies sont correctes et analysées</p>
                </div>
              </li>
-->
            </ul>
          </div>
          <div class="uk-background-contain" style="background-image: url('img/window.jpg');" uk-height-viewport></div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
  export default {
    name: 'Navbar',
  }

</script>

<style lang="scss" scoped>
  @import "../assets/scss/custom.scss"

</style>
