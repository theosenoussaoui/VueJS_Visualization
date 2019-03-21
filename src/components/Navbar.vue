<template>
  <nav class="uk-navbar-container uk-navbar-transparent uk-light" uk-navbar>
    <div class="uk-navbar-left">
      <a href class="uk-logo">
        <img src="img/logo.png" alt="Logo Daily Map">
      </a>
      <ul class="uk-navbar-nav">
        <li>
          <a href="#about" uk-toggle>À propos</a>
        </li>
        <li>
          <a href="#whoarewe" uk-toggle>Présentation</a>
        </li>
        <li>
          <a href="#faq" uk-toggle>FAQ</a>
        </li>
        <li>
          <a href="mailto:theosen95@gmail.com">Contact</a>
        </li>
      </ul>
    </div>
    <div class="uk-navbar-right">
      <ul class="uk-navbar-nav">
        <li>
          <a href="#" class uk-icon="facebook"></a>
        </li>
        <li>
          <a href="#" class uk-icon="twitter"></a>
        </li>
        <li>
          <a href="#" class uk-icon="instagram"></a>
        </li>
      </ul>
    </div>

    <div id="about" class="uk-modal-full" uk-modal>
      <div class="uk-modal-dialog">
        <nav class="uk-navbar-container" uk-navbar>
          <div class="uk-navbar-left">
            <a href class="uk-logo">
              <img src="img/logo_couleur.png" alt="Logo Daily Map">
            </a>
            <ul class="uk-navbar-nav">
              <li>
                <a href="#about" uk-toggle>À propos</a>
              </li>
              <li>
                <a href="#whoarewe" uk-toggle>Présentation</a>
              </li>
              <li>
                <a href="#faq" uk-toggle>FAQ</a>
              </li>
              <li>
                <a href="mailto:theosen95@gmail.com">Contact</a>
              </li>
            </ul>
          </div>
        </nav>
        <button class="uk-modal-close-full uk-close-large" type="button" uk-close></button>
        <div class="uk-grid-collapse uk-child-width-1-2@s uk-flex-middle" uk-grid>
          <div class="uk-padding-large">
            <h2 class="title">À propos</h2>
            <h3>Daily Map permet de visualiser en direct des articles et informations pour un futur départ dans un pays étranger.</h3>
            <h3>À l’aide d’une carte interactive, vous pouvez sélectionner un pays, puis découvrir en fonction de la nature de votre recherche des informations essentielles sur le pays.</h3>
            <h3>Vous souhaitez y aller pour le travail ? Les vacances ou bien pour vos études ? Notre site permet de répondre au mieux à vos questions en fonction de la catégorie sélectionnée.</h3>
            <h3>Alors n’hésitez pas à découvrir notre carte Daily Map !</h3>
          </div>
          <div class="uk-background-contain" style="background-image: url('img/presentation-2.jpg'); height:90vh"></div>
        </div>
      </div>
    </div>

    <div id="whoarewe" class="uk-modal-full" uk-modal>
      <div class="uk-modal-dialog">
        <nav class="uk-navbar-container" uk-navbar>
          <div class="uk-navbar-left">
            <a href class="uk-logo">
              <img src="img/logo_couleur.png" alt="Logo Daily Map">
            </a>
            <ul class="uk-navbar-nav">
              <li>
                <a href="#about" uk-toggle>À propos</a>
              </li>
              <li>
                <a href="#whoarewe" uk-toggle>Présentation</a>
              </li>
              <li>
                <a href="#faq" uk-toggle>FAQ</a>
              </li>
              <li>
                <a href="mailto:theosen95@gmail.com">Contact</a>
              </li>
            </ul>
          </div>
        </nav>
        <button class="uk-modal-close-full uk-close-large" type="button" uk-close></button>
        <div class="uk-grid-collapse uk-child-width-1-2@s uk-flex-middle uk-margin-top" uk-grid>
          <div class="uk-padding-large">
            <h3>En 2019, lors du Hackathon, nous avons créé une carte interactive pour le tourisme à destination des particuliers. Nous pensions qu’il fallait répondre à une vraie demande d’informations venant de toutes ces personnes voulant avoir des renseignements sur un pays étrangers.</h3>
          </div>
          <div class="uk-background-contain uk-margin-top" style="background-image: url('img/presentation-1.jpg'); background-size : 550px; min-height : 75vh"></div>
        </div>
        <div class="uk-grid-collapse uk-child-width-1-2@s uk-flex-middle" uk-grid>
          <div class="uk-background-contain" style="background-image: url('img/presentation-2.jpg'); min-height : 95vh"></div>
          <div class="uk-padding-large">
            <h3>Ensuite, il a été nécessaire d’apporter une réponse personnalisée à toutes les demandes en fonction de la nature du séjour. Nous avons défini 3 natures de voyage : pour les études à l'étranger, pour les vacances et pour le travail (courte et longue durée). Cela nous a permis de délivrer une réponse adaptée.</h3>
            <h3>Aujourd’hui, notre site compte plusieurs milliers d’articles de voyages.</h3>
          </div>
        </div>
        <div class="uk-grid-collapse uk-child-width-1-2@s uk-flex-middle uk-padding-middle" uk-grid>
          <div class="uk-padding-large">
            <h3>Notre objectif ?</h3>
            <h3>A chaque question d’un particulier, il faut déclencher une réponse réactive, adaptée et surtout de proximité.Nous orientons aussi les clients vers les sites partenaires afin de les aider et les conseiller au mieux dans la planification de leurs voyages.</h3>
          </div>
          <div class="uk-background-contain" style="background-image: url('img/presentation-3.jpg'); background-size : 450px; min-height : 55vh"></div>
        </div>
        <div class="uk-grid-collapse uk-child-width-1-2@s uk-flex-middle" uk-grid>
          <div class="uk-background-contain" style="background-image: url('img/presentation-4.jpg'); background-size : 350px; min-height : 75vh"></div>
          <div class="uk-padding-large">
            <h3>- Notre réseau de partenaires : Opodo,TripAdvisor,Welink, Hotels.com et AirBnB</h3>
            <h3>- La qualité de nos partenaires</h3>
          </div>
        </div>
      </div>
    </div>

    <div id="faq" class="uk-modal-full" uk-modal>
      <div class="uk-modal-dialog">
        <nav class="uk-navbar-container" uk-navbar>
          <div class="uk-navbar-left">
            <a href class="uk-logo">
              <img src="img/logo_couleur.png" alt="Logo Daily Map">
            </a>
            <ul class="uk-navbar-nav">
              <li>
                <a href="#about" uk-toggle>À propos</a>
              </li>
              <li>
                <a href="#whoarewe" uk-toggle>Présentation</a>
              </li>
              <li>
                <a href="#faq" uk-toggle>FAQ</a>
              </li>
              <li>
                <a href="mailto:theosen95@gmail.com">Contact</a>
              </li>
            </ul>
          </div>
        </nav>
        <button class="uk-modal-close-full uk-close-large" type="button" uk-close></button>
        <div class="uk-grid-collapse uk-child-width-1-2@s uk-flex-middle" uk-grid>
          <div class="uk-padding-large">
            <ul uk-accordion>
              <li>
                <a class="uk-accordion-title" href="#">
                  <h3>Qu’est-ce-que Daily Map ?</h3>
                </a>
                <div class="uk-accordion-content">
                  <p>
                    <a href="#whoarewe" uk-toggle>Voir la page de présentation</a>
                  </p>
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
              <li>
                <a class="uk-accordion-title" href="#">
                  <h3>Quelles sont les catégories d’articles ?</h3>
                </a>
                <div class="uk-accordion-content">
                  <ul>
                    <li>À la une</li>
                    <li>Économie</li>
                    <li>Divertissement</li>
                    <li>Santé</li>
                    <li>National</li>
                    <li>Sports</li>
                    <li>Science</li>
                    <li>International</li>
                  </ul>
                </div>
              </li>
              <li>
                <a class="uk-accordion-title" href="#">
                  <h3>Comment sont classés les articles ?</h3>
                </a>
                <div class="uk-accordion-content">
                  <p>Les articles sont classés par statut. C’est à dire que vous avez la possibilité de choisir entre Travail, Étude ou bien Voyages.</p>
                </div>
              </li>
              <li>
                <a class="uk-accordion-title" href="#">
                  <h3>Les données sont-elles mise à jour ?</h3>
                </a>
                <div class="uk-accordion-content">
                  <p>Oui toutes les informations fournies sont correctes et analysées</p>
                </div>
              </li>
            </ul>
          </div>
          <div class="uk-background-contain" style="background-image: url('img/faq.jpg');" uk-height-viewport></div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
  export default {
    name: "Navbar"
  };

</script>

<style lang="scss" scoped>
  @import "../assets/scss/navbar.scss";
</style>
