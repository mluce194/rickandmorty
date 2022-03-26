<template>
  <Header
    title1="Rick & Morty - Character search form"
    title2="Look for Rick and Morty Characters by searching through our database"
  />

  <SearchCharacterForm></SearchCharacterForm>
</template>

<script>
import Header from "./components/Header.vue";
import SearchCharacterForm from "./components/SearchCharacterForm.vue";

import "./styles.css";

export default {
  name: "App",
  components: {
    Header,
    SearchCharacterForm,
  },
};
</script>
