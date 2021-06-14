<template>
  <main>
    <transition name="fade">
      <Loader v-if="!isLoaded" />
    </transition>
      <div else class="container">
          <div class="row">
              <div class="col-6 col-md-4 col-lg-2" 
              v-for="(disc, index) in filter" 
              :key="index"
              >
              <Card :item="disc" />
              </div>    
          </div>
      </div> 
  </main>     
</template>

<script>
import Card from "./Card";
import Loader from "./Loader";
import axios from "axios";
export default {
        name: "Main",
        components: {
          Card,
          Loader
        },
        data() {
          return {
              discArray: [],
              isLoaded: false
          };
        },
        props: {
            valoreSelezionato: String,
            chiaveDiSelezione: String
        },
        methods: {},
        computed: {
          filter() {
              if (this.valoreSelezionato != "all") {
                  var array = this.discArray.filter((element) => {
                      return element[this.chiaveDiSelezione] == this.valoreSelezionato;
                  });
              } else {
                  array = this.discArray;
              }
              return array;
          }
        },
        created() {
            axios
              .get("https://flynn.boolean.careers/exercises/api/array/music")
              .then((response) => {
                  this.discArray = response.data.response;
                  this.$emit("passoArrayGenerale", this.discArray);
                
                setTimeout(() => {
                  console.log((this.isLoaded = true));
                },1500);
              });
        }
};
</script>

<style lang="scss" scoped>
@import "../style/variables";
main {
  padding-top: 5%;
  min-height: calc(100vh - #{$headerHeight});
  background-color: $mainBlue;
  .row {
    justify-content: center;
    & > div {
      margin: 1% 1%;
    }
  }
}
.fede-leave-active {
  transition: opacity 0,6s;
}
.fede-leave-to {
  opacity: 0;
}
</style>