<template>
  <section v-if="!loading" class="container">
    <div
      v-for="(item, index) in dischiArray"
      :key="index"
      class="disco-singolo"
    >
      <Disco :info="item" />
    </div>
  </section>
  <Loader v-else />
</template>

<script>
import axios from "axios";
import Disco from "../common/Disco.vue";
import Loader from "../common/Loader.vue";

export default {
  name: "listaDischi",
  components: {
    Disco,
    Loader,
  },
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      dischiArray: [],
      loading: true,
    };
  },
  methods: {
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

.disco-singolo {
  background-color: $main_color;
  width: 200px;
  min-height: 300px;
  margin-bottom: 20px;
}

section.container {
  width: 80%;
  margin: 70px auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
</style>