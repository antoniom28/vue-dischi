<template>
  <div class="container-cerca">
    <span @click="openSelect('genere')">Filtra per genere</span>
    <br><br>
    <span @click="openSelect('artista')">Filtra per Artista</span>
    <br><br>
    <select
      v-if="selectType != ''"
      v-model="selectValue"
      @change="$emit('filtra', selectValue,selectType)"
      name=""
      id="filtra-dischi"
    >
      <option value=""></option>
      <option
        v-for="(item, index) in noRepeat"
        :key="index"
        :value="item"
      >
        {{ item }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "Cerca",
  data() {
    return {
      selectValue: "",
      selectType: "",
    };
  },
  methods: {
      openSelect(type){
          this.selectType = type;
      },
  },
  computed: {
    //genera le option in base ai generi prese dall'API, senza ripetere
    //più option per gli stessi generi, codice da migliorare
    //inoltre filtra a seconda di cosa abbiamo scelto,
    //se per genere, o artista, anche se in questo caso c'è un brano per artista
    noRepeat() {
      let temp = [];
      let error = [];
      for (let i = 0; i < this.dischiArr.length; i++) {
        if(this.selectType == 'genere')
            error = temp.filter(str => str == this.dischiArr[i].genre);
        else
            error = temp.filter(str => str == this.dischiArr[i].author);

        if (error.length == 0){
            if(this.selectType == 'genere')
                temp.push(this.dischiArr[i].genre);
            else
                temp.push(this.dischiArr[i].author);
            }
      }
      return temp;
    },
  },
  props: {
    dischiArr: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/style/partials/variables.scss";
span{
    color: white;
    margin: 0 5px;
    cursor: pointer;
}

.container-cerca{
    text-align: center;
    margin-top: 30px;
}

select{
    width: 140px;
    background-color: $main_color;
    color: white;
    padding: 0 5px;
}
</style>