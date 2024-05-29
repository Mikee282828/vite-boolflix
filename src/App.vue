<script>
import store from "./data/store.js";
import Movies from "./components/Movies.vue";
import Tv from "./components/Tv.vue";
import AppHeader from "./components/AppHeader.vue";
export default {
  components: {
    Movies,
    Tv,
    AppHeader
  },
  data() {
    return {
      store,
    }
  },
  created() {

  }
}
</script>

<template>

  <AppHeader />

  <Movies />
  <Tv />

</template>

<style scoped></style>
