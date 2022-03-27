<template>
  <Header
    title1="Rick & Morty - Character search form"
    title2="Look for Rick and Morty Characters by searching through our database"
    :image="require('./assets/img/banniere.jpeg')"
    imageDescription="Rick and Morty character search form"
  />

  <SearchCharacterForm></SearchCharacterForm>
  <Footer texte="Powered by VueJS, TailwndCSS & Apollo" credits="Photo credits: Wikipedia Commons"></Footer>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import SearchCharacterForm from "./components/SearchCharacterForm.vue";

import "./styles.css";

export default {
  name: "App",
  components: {
    Header,
    SearchCharacterForm,
    Footer
  },
};
</script>
