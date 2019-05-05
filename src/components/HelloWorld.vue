<template>
<div class="main-app">
  <div class="carousell">
    <div id="prevImg" @click.prevent="prevImage">
      <i class="fa fa-chevron-left" aria-hidden="true"></i>
    </div>
    <div class="container">
      <div class="image-box">
        <img id="image" :src="firstImg.src" class="img-fluid">
      </div>
      <div id="speech" class="speech">
        <span v-for="text in firstImg.text">{{text}}</span>
      </div>
    </div>
    <div id="nextImg" @click.prevent="nextImage">
      <i class="fa fa-chevron-right" aria-hidden="true"></i>
    </div>
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
          text: ['Sinh nhật vui vẻ nhen người!!!', '(bấm mũi tên để xem hình khác nha)']
        },
      listImgs: [
        {
          src: require('../assets/hpbd.gif'),
          text: ['Sinh nhật vui vẻ nhen người!!!', '(bấm mũi tên để xem hình khác nha)']
        },
        {
          src: require('../assets/hpbd2.gif'),
          text: ['*Thổi kèn* Toe toe toe']
        },
        {
          src: require('../assets/db_pig_nose.png'),
          text: ['Thấy hình trên giống mi hong???', 'Heooooo']
        },
        {
          src: require('../assets/hpbd5.gif'),
          text: ['Nhớ ăn uống đầy đủ để còn uống thuốc với có sức làm nha']
        },
        {
          src: require('../assets/ravee.gif'),
          text: ['Giữ gìn sức khoẻ cho tốt nhe sắp thi rồi đó.', 'Chúc mi đạt được những gì mình mong muốn.']
        },
        {
          src: require('../assets/duyen.jpg'),
          text: ['Thích tấm hình này của mi nhất.','Lúc nào cũng vui cười như vầy nhé!']
        },
        {
          src: require('../assets/heo.png'),
          text: ['I know this can\'t help or fix what you are going through.', 'These\'re just words on paper.', 'But maybe it will remind you that I am still here...', 'and so are you.']
        },
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
  font-family: 'Itim', cursive;

  @media (max-width: 600px) {
    padding: 25px 0;
  }


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
      max-width: 740px;
    }

    .speech {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      flex: 1;
      border: 1px solid #ede;
      border-radius: 6px;
      min-height: 90px;

      span {
        font-size: 1.55em;
      }
    }

    #prevImg, #nextImg {
      margin: 0 20px;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      flex: 1;
      min-width: 40px;
      max-width: 80px;

      i {
        display: flex;
        justify-content: center;
        align-items: center;
        color: white;
        background: #f4ba05;
        border-radius: 20px;
        height: 40px;
        width: 40px;
        transition: all .15s ease-in;
      }

      &:hover {
        i {
          transform: scale(1.3, 1.3);
        }
      }
    }
  }
}
</style>
