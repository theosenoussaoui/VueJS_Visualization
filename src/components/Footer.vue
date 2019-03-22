<template>
  <div class="footer uk-light uk-text-center">
    <button class="uk-button uk-button-default" type="button">Liste des pays disponibles</button>
    <div uk-dropdown>
      <ul class="uk-nav uk-dropdown-nav" id="listCountry">
      </ul>
    </div>

    <!-- ----------------------------------------------- -->

    <!-- This is a button toggling the modal with the default close button -->
    <button
      class="uk-button uk-button-default uk-margin-small-right uk-margin-small-left"
      type="button"
      uk-toggle="target: #modal-container"
    >Bouton modale choix pays</button>

    <!-- This is the modal with the default close button -->
    <div id="modal-container" class="uk-modal-container" uk-modal>
      <div class="uk-modal-dialog uk-modal-body" uk-overflow-auto>
        <h2 class="uk-modal-title">Nom du pays choisi.</h2>

        <div class="uk-text-center">
          <ul class="uk-child-width-expand" uk-tab>
            <li class="uk-active">
              <button class="uk-button uk-button-default uk-margin-small-right">
                <img src="img/vacances.jpg" alt="Vacances">
              </button>
            </li>
            <li>
              <button class="uk-button uk-button-default uk-margin-small-right">
                <img src="img/education.jpg" alt="Education">
              </button>
            </li>
            <li>
              <button class="uk-button uk-button-default uk-margin-small-right">
                <img src="img/business.jpg" alt="Business">
              </button>
            </li>
            <li>
              <button class="uk-button uk-button-default uk-margin-small-right">
                <img src="img/news.jpg" alt="News">
              </button>
            </li>
          </ul>

          <ul class="uk-switcher uk-margin">
            <li>
              <div class="uk-child-width-1-3 uk-grid-small uk-grid-match" uk-grid>
                <div>
                  <div class="uk-card uk-card-default uk-margin-small">
                    <div class="uk-card-header">
                      <div class="uk-grid-small uk-flex-middle" uk-grid>
                        <div class="uk-width-auto">
                          <img class="uk-border-circle" width="70" height="70" src="img/avatar.jpg">
                        </div>
                        <div class="uk-width-expand">
                          <h3 class="uk-card-title uk-margin-remove-bottom">Titre de l'article</h3>
                          <!-- <p class="uk-text-meta uk-margin-remove-top"><time datetime="2016-04-01T19:00">April 01, 2016</time></p> -->
                        </div>
                      </div>
                    </div>
                    <div class="uk-card-body">
                      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt.</p>
                    </div>
                    <div class="uk-card-footer">
                      <a href="#" class="uk-button uk-button-text">Lire l'article</a>
                    </div>
                  </div>
                </div>

                <div>
                  <div class="uk-card uk-card-default uk-margin-small">
                    <div class="uk-card-header">
                      <div class="uk-grid-small uk-flex-middle" uk-grid>
                        <div class="uk-width-auto">
                          <img class="uk-border-circle" width="70" height="70" src="img/avatar.jpg">
                        </div>
                        <div class="uk-width-expand">
                          <h3 class="uk-card-title uk-margin-remove-bottom">Titre de l'article</h3>
                          <!-- <p class="uk-text-meta uk-margin-remove-top"><time datetime="2016-04-01T19:00">April 01, 2016</time></p> -->
                        </div>
                      </div>
                    </div>
                    <div class="uk-card-body">
                      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt.</p>
                    </div>
                    <div class="uk-card-footer">
                      <a href="#" class="uk-button uk-button-text">Lire l'article</a>
                    </div>
                  </div>
                </div>

                <div>
                  <div class="uk-card uk-card-default uk-margin-small">
                    <div class="uk-card-header">
                      <div class="uk-grid-small uk-flex-middle" uk-grid>
                        <div class="uk-width-auto">
                          <img class="uk-border-circle" width="70" height="70" src="img/avatar.jpg">
                        </div>
                        <div class="uk-width-expand">
                          <h3 class="uk-card-title uk-margin-remove-bottom">Titre de l'article</h3>
                          <!-- <p class="uk-text-meta uk-margin-remove-top"><time datetime="2016-04-01T19:00">April 01, 2016</time></p> -->
                        </div>
                      </div>
                    </div>
                    <div class="uk-card-body">
                      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt.</p>
                    </div>
                    <div class="uk-card-footer">
                      <a href="#" class="uk-button uk-button-text">Lire l'article</a>
                    </div>
                  </div>
                </div>
              </div>
            </li>
            <li>Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</li>
            <li>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur, sed do eiusmod.</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { objectCountries } from "../assets/js/objectCountries.js";

export default {
  name: "Footer",
  mounted() {
    var str = '';
    for (const key in objectCountries) {
      if (objectCountries.hasOwnProperty(key)) {
        console.log(objectCountries[key]);
        str += "<li> <datagoto=" + objectCountries[key]['nameFr'] + ">" + objectCountries[key]['nameFr'] + "</datagoto></li>";
      }
    } 

    var lCountry = document.getElementById('listCountry');
    console.log(lCountry);
    lCountry.innerHTML = str;
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/custom.scss";
@import "../assets/scss/footer.scss";
</style>
