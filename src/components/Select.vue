<template>
  <select
    class="from-select"
    @change="
    selectOptionReturn($event);
    $emit('selectOptionReturn', valoreSelezionato, chiaveDiSelezione);
    "
  >
    <option selected disabled>{{ mainText}}</option>
    <option value="all">Tutti</option>
    <option
      v-for="(element, index) in finalArray"
      :key="index"
      :value="element"
    >
      {{ element }}
    </option>
  </select>
</template>

<script>
export default {
        name: "Select",
        props: {
            mainText: String,
            optionArray: Array,
            chiaveDiSelezione: String
        },
        data() {
          return {
              valoreSelezionato: undefined
          };
        },
        methods: {
            selectOptionReturn(event) {
              this.valoreSelezionato = event.target.value;
            },
            oggettoEstratto(element) {
              if ((element = !undefined)) {
                return element[this.chiaveDiSelezione];
              }
            }
        },
        computed: {
          finalArray() {
            var array = [];
            if (this.optionArray.lenght > 1) {
              array = this.optionArray.map(
                  (element) => element[this.chiaveDiSelezione]
              );
            }
            return [...new Set(array)];
          }
        }
};
</script>

<style lang="scss" scoped>
.from-select {
  align-self: center;
  width: 210px;
  height: 80%;
  margin-left: auto;
}
</style>