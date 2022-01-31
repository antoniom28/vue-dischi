<template>
  <main class="container">
    <listaDischi />
  </main>
</template>

<script>
import listaDischi from "../section/listaDischi.vue";

export default {
  name: "Main",
  components: {
    listaDischi,
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/style/partials/variables.scss";
main.container {
  display: inline-block;
  width: 100%;
  background-color: $bg_color;
}
</style>