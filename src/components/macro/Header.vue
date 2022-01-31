<template>
    <header class="container">
        <img class="logo" src="../../assets/img/logo.png" alt="">
    </header>
</template>

<script>
export default {
    name: 'Header',
}
</script>

<style lang="scss" scoped>
@import '../../assets/style/partials/variables.scss';
.container{
    background-color: $main_color;
}

img.logo{
    width: 50px;
    margin: 5px 15px;
}
</style>