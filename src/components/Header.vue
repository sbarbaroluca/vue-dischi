<template>
  <header class="d-flex">
      <img src="../assets/spotify.png" alt="Spotify" />
      <div class="selects d-flex">
      <Select
       main-text="Seleziona un genere"
       :optionArray="arrayGeneralePieno"
       :chiave-select="chiaveSelect1"
       @selectOptionReturn="passoValore"
       />
       <Select
       main-text="Seleziona un artista"
       :optionArray="arrayGeneralePieno"
       :chiave-select="chiaveSelect2"
       @selectOptionReturn="passoValore"
       />
      </div>
  </header>
</template>

<script>
import Select from "./Select";
export default {
        name: "Header",
        components: {
          Select
        },
        data() {
          return {
              chiaveSelect1: "genre",
              chiaveSelect2: "author"
          };
        },
        props: {
          arrayGeneralePieno: Array
        },
        methods: {
            passoValore(valore, chiaveDiSelezione) {
                this.$emit("passoValore", valore, chiaveDiSelezione);
            }
        }
};
</script>

<style lang="scss" scoped>
@import "../style/variables";
header {
  justify-content: space-between;
  height: 100px;
  padding: 20px;
  background-color: $mainGrey;
  .selects {
    width: 25%;
  }
  img {
    height: 100%;
  }
}
</style>