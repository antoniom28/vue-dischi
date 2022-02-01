<template>
  <section v-if="!loading">
    <Cerca 
    :dischiArr="dischiArray" 
    @filtra="filtraDischi" 
    />
    <div class="container">
        <Disco :info="item"
          v-for="(item, index) in dischiFiltrati"
          :key="index"
         />
    </div>
  </section>
  <Loader v-else />
</template>

<script>
import axios from "axios";
import Disco from "../common/Disco.vue";
import Loader from "../common/Loader.vue";
import Cerca from "../common/Cerca.vue";

export default {
  name: "listaDischi",
  components: {
    Disco,
    Loader,
    Cerca,
  },
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      dischiArray: [],
      loading: true,
      inputOption: "",
      inputType: "",
    };
  },
  computed: {
    dischiFiltrati() {
      return this.dischiArray.filter((disc) => {
        if(this.inputType == 'genere')
          return disc.genre.includes(this.inputOption);
        else
          return disc.author.includes(this.inputOption);
      });
    },
  },
  methods: {
    filtraDischi(filt,type) {
      this.inputOption = filt;
      this.inputType = type;
    },
    getDischi() {
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
    },
  },
  created: function () {
    this.getDischi();
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/style/partials/variables.scss";

div.container {
  width: 80%;
  margin: 70px auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
</style>