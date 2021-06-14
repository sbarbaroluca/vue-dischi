<template>
  <div id="app">
        <Header
          :arrayGeneralePieno="arrayGenerale"
          @passoValore="salvoValore"
        />
        <Main
          @passoArrayGenerale="salvoArrayGenerale"
          :valoreSelezionato="valoreSelezionato"
          :chiaveDiSelezione="chiaveDiSelezione"
        />
  </div>
</template>

<script>
import Header from "./components/Header";
import Main from "./components/Main";
export default {
  name: "App",
  components: {
        Header,
        Main
  },
  data() {
    return {
        genreArray: [],
        valoreSelezionato: undefined,
        chiaveDiSelezione: "all",
        arrayGenerale: []
    };
  },
  methods: {
    salvoValore(valore, chiaveDiSelezione) {
      this.valoreSelezionato = valore;
      if (chiaveDiSelezione != undefined) {
        this.chiaveDiSelezione = chiaveDiSelezione;
      }
    },
    salvoArrayGenerale(array) {
      this.arrayGenerale = array;
    }
  }
};
</script>

<style lang="scss">
@import "./style/general";
</style>
