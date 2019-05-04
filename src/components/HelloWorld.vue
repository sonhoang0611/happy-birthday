<template>
<div class="main-app">
  <div class="carousell">
    <div id="prevImg" @click.prevent="prevImage"><</div>
    <div class="container">
      <div class="image-box">
        <img id="image" :src="firstImg.src" class="img-fluid">
      </div>
      <div id="speech" class="speech">
        <span>{{firstImg.text}}</span>
      </div>
    </div>
    <div id="nextImg" @click.prevent="nextImage">></div>
  </div>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      firstImg: {
          src: require('../assets/hpbd.gif'),
          text: 'Sinh nhật vui vẻ nghen!!!'
        },
      listImgs: [
        {
          src: require('../assets/hpbd.gif'),
          text: 'Sinh nhật vui vẻ nghen!!!'
        },
        {
          src: require('../assets/hpbd2.gif'),
          text: 'Sinh nhật vui vẻ nghen 2!!!'
        },
        {
          src: require('../assets/db_pig_nose.png'),
          text: 'Sinh nhật vui vẻ nghen 3!!!'
        },
        {
          src: require('../assets/ravee.gif'),
          text: 'Sinh nhật vui vẻ nghen 4!!!'
        }
      ]
    }
  },
  methods: {
    nextImage(event) {
      event.stopPropagation();
      const self = this;
      for (let i = 0, len = this.listImgs.length; i < len; i++){
        if (this.firstImg.src === this.listImgs[i].src) {
          let j = ++i;
          Object.assign(this.firstImg, this.listImgs[j % len]);
        }
      }
    },
    prevImage(event) {
      event.stopPropagation();
      for (let len = this.listImgs.length, i = len - 1; i > -1; i--){
        if (this.firstImg.src === this.listImgs[i].src) {
          let j = (i % len === 0) ? (len - 1) : (--i);
          Object.assign(this.firstImg, this.listImgs[j]);
        }
      }
    }
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
  background: url(../assets/birthday-cake.jpg);
  background-position: 50% 50%;
  background-size: cover;
  padding: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;

  .carousell {
    height: 100%;
    display: flex;

    .container {
      padding: 30px;
      max-width: 825px;
      border-radius: 8px;
      background: white;
      box-shadow: 1px 1px 15px 1px rgba(0,0,0,0.1);
      border-color: #eee;
      display: flex;
      flex-direction: column;
    }

    .image-box {
      max-width: 800px;
      img {
        border: 1px solid #ede;
        border-radius: 6px;
      }
    }
    .speech {
      display: flex;
      flex: 1;
      justify-content: center;
      align-items: center;
      font-family: 'Itim', cursive;

      span {
        font-size: 2em;
        font-weight: 600;
      }
    }

    #prevImg, #nextImg {
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      flex: 1;
      min-width: 40px;
      max-width: 80px;
    }
  }
}
</style>
