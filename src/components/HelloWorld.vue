<template>
<div class="main-app">
  <div class="carousell container">
    <div class="image-box">
      <img src="../assets/img/hpbd.gif" class="img-fluid">
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted() {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.main-app {
  height: 100%;
  width: 100%;
  margin: 0;
  background: url(../assets/img/birthday-cake.jpg);
  position: 50% 50%;
  background-size: cover;
  padding: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;

  .carousell {
    height: 100%;
    max-width: 825px;
    padding: 30px;
    border-radius: 8px;
    background: white;
    box-shadow: 1px 1px 15px 1px rgba(0,0,0,0.1);
    border-color: #eee;
  }
}
</style>
