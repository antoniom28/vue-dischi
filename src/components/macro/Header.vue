<template>
  <header class="container">
    <img class="logo" src="../../assets/img/logo.png" alt="" />
  </header>
</template>

<script>

export default {
  name: "Header",
};
</script>

<style lang="scss" scoped>
@import "../../assets/style/partials/variables.scss";

.fa-filter{
  color:green;
  display: none;
  font-size: 30px;
  margin: 0 15px;
  cursor: pointer;
}

.container {
  background-color: $main_color;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

img.logo {
  width: 50px;
  margin: 5px 15px;
}
</style>