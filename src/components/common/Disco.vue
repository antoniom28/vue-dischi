<template>
    <div class="container-disco">
        <img :src="info.poster" :alt="info.title">
        <h3>{{info.title}}</h3>
        <div>
            {{info.author}}
            <br>
            {{info.year}}
        </div>
    </div>
</template>

<script>
export default {
    name: 'Disco',
    props: {
        info : Object,
    },
}
</script>

<style lang="scss" scoped>
@import "../../assets/style/partials/variables.scss";

div.container-disco{
    background-color: $main_color;
    text-align: center;
    width: 200px;
    min-height: 300px;
    margin-bottom: 20px;
    padding: 10px 15px;

    div,h3{
        margin: 15px 0;
    }
    div{
        color: grey;
    }

    h3{
        color: white;
        text-transform: uppercase;
    }
}

img{
    width: 100%;
    box-shadow: 0 0 6px 3px rgba(0, 0, 0, 0.6);
}
</style>