<template>
  <div class="loader">
    <span>
      <i class="fas fa-compact-disc"></i>
    </span>
  </div>
</template>

<script>
export default {
  name: "Loader",
};
</script>

<style lang="scss" scoped>
div.loader {
  text-align: center;
  height: 100vh;
  margin-top: 25vh;
  span {
    font-size: 4em;
    animation: spin 1s linear infinite;
    display: inline-block;
  }
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
  from {
    transform: rotate(0deg);
  }
}
</style>