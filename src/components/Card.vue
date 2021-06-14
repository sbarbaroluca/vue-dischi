<template>
  <div class="card text-center">
      <div class="img-container">
          <img :src="item.poster" alt="item.title" />
      </div>
      <h2>{{ item.title }}</h2>
      <h5>{{ item.author }}</h5>
      <h6>{{ item.year }}</h6>
  </div>
</template>

<script>
export default {
        name: "Card",
        props: {
            item: Object
        }
};
</script>

<style lang="scss" scoped>
@import "../style/variables";
.card {
  height: 100%;
  background-color: $mainGrey;
  cursor: pointer;
  .img-container {
    padding: 20px;
    img {
      width: 100%;
    }
  }
  h2 {
    color: #fff;
    text-transform: uppercase;
    font-weight: 500;
    font-size: 16px;
  }
  h5,
  h6 {
    font-weight: 400;
    font-size: 15px;
    color: grey;
  }
}
</style>