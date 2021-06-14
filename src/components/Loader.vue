<template>
  <div>
    <div class="loader-container">
        <img src="../assets/charger.gif" alt="" />
    </div>
   </div>  
</template>

<script>
export default {
        name: "Loader"
};
</script>

<style lang="scss" scoped>
@import "../style/mixins";
div {
  @include loaderPlacement;
  .loader-container {
      @include flex-center("both");
  }
}
</style>