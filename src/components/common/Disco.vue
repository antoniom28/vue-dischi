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
div.container-disco{
    text-align: center;
    width: 80%;
    margin: 0 auto;
    padding: 15px 0;

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