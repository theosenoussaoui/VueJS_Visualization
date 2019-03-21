<template>
  <div class="footer uk-light">
    <button class="uk-button uk-button-default" type="button">Liste des pays disponibles</button>
    <div uk-dropdown>
      <ul class="uk-nav uk-dropdown-nav">
        <!--        <li class="uk-active"><a href="#">Active</a></li>-->
        <li><a href="#">Item</a></li>
        <!--        <li class="uk-nav-header">Header</li>-->
        <li><a href="#">Item</a></li>
        <li><a href="#">Item</a></li>
        <li><a href="#">Item</a></li>
        <li><a href="#">Item</a></li>
        <li><a href="#">Item</a></li>
        <!--        <li class="uk-nav-divider"></li>-->
        <li><a href="#">Item</a></li>
      </ul>
    </div>



    <!-- ----------------------------------------------- -->



    <!-- This is a button toggling the modal with the default close button -->
    <button class="uk-button uk-button-default uk-margin-small-right uk-margin-small-left" type="button" uk-toggle="target: #modal-container">Bouton modale choix pays</button>

    <!-- This is the modal with the default close button -->
    <div id="modal-container" class="uk-modal-container" uk-modal>
      <div class="uk-modal-dialog uk-modal-body" uk-overflow-auto>
        <h2 class="uk-modal-title">Nom du pays choisi.</h2>
        <!--
        <button class="uk-modal-close-default" type="button" uk-close></button>
        <ul class = "uk-flex-center" uk-tab>
          <li><a href="#">Item</a></li>
          <li><a href="#">Item</a></li>
          <li><a href="#">Item</a></li>
        </ul>
        -->

        <div class="uk-text-center">
          <button class="uk-button uk-button-default uk-margin-small-right">
            <img src="img/logo_couleur.png" alt="Logo Couleur Daily Map" width="150" />
          </button>
          <button class="uk-button uk-button-default uk-margin-small-right">
            <img src="img/logo_couleur.png" alt="Logo Couleur Daily Map" width="150" />
          </button>
          <button class="uk-button uk-button-default uk-margin-small-right">
            <img src="img/logo_couleur.png" alt="Logo Couleur Daily Map" width="150" />
          </button>
          <button class="uk-button uk-button-default uk-margin-small-right">
            <img src="img/logo_couleur.png" alt="Logo Couleur Daily Map" width="150" />
          </button>

          <hr class="uk-margin-top">
          <div class="uk-child-width-1-3 uk-grid-small uk-grid-match" uk-grid>

            <div>
              <div class="uk-card uk-card-default uk-margin-small">
                <div class="uk-card-header">
                  <div class="uk-grid-small uk-flex-middle" uk-grid>
                    <div class="uk-width-auto">
                      <img class="uk-border-circle" width="40" height="40" src="images/avatar.jpg">
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
                      <img class="uk-border-circle" width="40" height="40" src="images/avatar.jpg">
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
                      <img class="uk-border-circle" width="40" height="40" src="images/avatar.jpg">
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
                      <img class="uk-border-circle" width="40" height="40" src="images/avatar.jpg">
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
                      <img class="uk-border-circle" width="40" height="40" src="images/avatar.jpg">
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
                      <img class="uk-border-circle" width="40" height="40" src="images/avatar.jpg">
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

        </div>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'Footer',
  }

</script>

<style lang="scss" scoped>
  @import "../assets/scss/footer.scss"

</style>
