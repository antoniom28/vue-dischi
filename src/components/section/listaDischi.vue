<template>
    <section v-if="!loading" class="container">
            <div 
            v-for="(item,index) in dischiArray" :key="index"
            class="disco-singolo">
                <Disco :info="item"/>
            </div>
    </section>
    <div class="loader" v-else>
        <span>
            <i class="fas fa-compact-disc"></i>
        </span>
    </div>
</template>

<script>
import axios from 'axios';
import Disco from '../common/Disco.vue'

export default {
    name: 'listaDischi',
    components: {
        Disco,
    },
    data(){
        return{
            apiUrl : "https://flynn.boolean.careers/exercises/api/array/music",
            dischiArray : [],
            loading : true,
        }
    },
    methods: {
    getDischi (){
            axios
            .get(this.apiUrl)
            .then((dischi) => {
                    this.dischiArray = dischi.data.response;
                    setTimeout(() => {
                        this.loading = false;
                    }, 1200);
            })
            .catch(function (error) {
                console.log(error);
            });
        } 
    },
    created: function() {
        this.getDischi();
    }
}
</script>

<style lang="scss" scoped>
@import '../../assets/style/partials/variables.scss';

.disco-singolo{
    background-color: $main_color;
    width: 200px;
    min-height: 300px;
    margin-bottom: 20px;
}

section.container{
    width: 80%;
    margin: 70px auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;

}

div.loader{
        text-align: center;
        height: 100vh;
        margin-top: 25vh;
        span{
            font-size: 4em;
            animation: spin 1s linear infinite;
            display: inline-block;
        }
}

@keyframes spin {
    to{
        transform: rotate(360deg);
    }
    from{
        transform: rotate(0deg);
    }
}
</style>