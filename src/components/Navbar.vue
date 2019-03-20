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
            <h2>Daily Map est une plateforme interactive qui a pour but de rendre plus facilement accessible une information sur une destination en particulier.</h2>
            <h2>En effet, un internaute consulte au moins 8 sites avant se décider à réserver.</h2>
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
            <h2>Daily Map est une plateforme interactive qui a pour but de rendre plus facilement accessible une information sur une destination en particulier.</h2>
            <h2>En effet, un internaute consulte au moins 8 sites avant se décider à réserver.</h2>
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
                <a class="uk-accordion-title" href="#"><h3>Lorem ipsum dolor sit amet, consectetur adipiscing elit ?</h3></a>
                <div class="uk-accordion-content">
                  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                </div>
              </li>
              <li>
                <a class="uk-accordion-title" href="#"><h3>Lorem ipsum dolor sit amet, consectetur adipiscing elit ?</h3></a>
                <div class="uk-accordion-content">
                  <p>Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor reprehenderit.</p>
                </div>
              </li>
              <li>
                <a class="uk-accordion-title" href="#"><h3>Lorem ipsum dolor sit amet, consectetur adipiscing elit ?</h3></a>
                <div class="uk-accordion-content">
                  <p>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat proident.</p>
                </div>
              </li>
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
