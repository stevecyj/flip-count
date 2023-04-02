<template>
  <div>
    <h1>{{ msg }}</h1>
    <div class="flip" :class="[flipType,{'go':isFlipping}]">
      <div class="digital front " :class="classNumber(frontText)"></div>
      <div class="digital back " :class="classNumber(backText)"></div>
    </div>
    <div class="btn-con">
      <button id="btn1" @click="flipDown">向下翻+1</button>
      <button id="btn2" @click="flipUp">向上翻-1</button>
    </div>
  </div>
</template>

<script>

export default {
  name: "FlipClock",
  props: {
    msg: String,
  },
  data() {
    return {
      isFlipping: false,
      flipType: 'down',
      count: 0,
      frontText: 0,
      backText: 1,
      duration: 600
    };
  },
  computed: {},
  methods: {
    flipDown() {
      if (this.isFlipping) {
        return false;
      }

      this.backText = this.frontText >= 9 ? 0 : this.frontText + 1;
      this.isFlipping = true;

      setTimeout(() => {
        this.isFlipping = false;
        this.frontText = this.backText;

      }, 600);
    },
    flipUp() {
    },
    classNumber(number) {
      return `number${number}`;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/*flipper 外框*/
.flip {
  display: inline-block;
  position: relative;
  width: 60px;
  height: 100px;
  line-height: 100px;
  border: solid 1px #000;
  border-radius: 10px;
  background: #fff;
  font-size: 66px;
  color: #fff;
  box-shadow: 0 0 6px rgba(0, 0, 0, 0.5);
  text-align: center;
  font-family: "Helvetica Neue", serif;
}

/*產生4張轉牌*/
.flip .digital:before,
.flip .digital:after {
  content: "";
  position: absolute;
  left: 0;
  right: 0;
  background: #000;
  overflow: hidden;
  box-sizing: border-box;
}

.flip .digital:before {
  top: 0;
  bottom: 50%;
  border-radius: 10px 10px 0 0;
  border-bottom: solid 1px #666; /*水平折線*/
}

.flip .digital:after {
  top: 50%;
  bottom: 0;
  border-radius: 0 0 10px 10px;
  line-height: 0; /*把上下數字接在一起*/
}

/*牌上的數字*/
.flip .number0:before,
.flip .number0:after {
  content: "0";
}

.flip .number1:before,
.flip .number1:after {
  content: "1";
}

.flip .number2:before,
.flip .number2:after {
  content: "2";
}

.flip .number3:before,
.flip .number3:after {
  content: "3";
}

.flip .number4:before,
.flip .number4:after {
  content: "4";
}

.flip .number5:before,
.flip .number5:after {
  content: "5";
}

.flip .number6:before,
.flip .number6:after {
  content: "6";
}

.flip .number7:before,
.flip .number7:after {
  content: "7";
}

.flip .number8:before,
.flip .number8:after {
  content: "8";
}

.flip .number9:before,
.flip .number9:after {
  content: "9";
}

/*向下翻*/
.flip.down .front:before {
  z-index: 3;
}

.flip.down .back:after {
  z-index: 2;
  transform-origin: 50% 0;
  transform: perspective(160px) rotateX(180deg);
}

.flip.down .front:after,
.flip.down .back:before {
  z-index: 1;
}

/*旋轉效果*/
.flip.down.go .front:before {
  transform-origin: 50% 100%;
  animation: frontFlipDown 0.6s ease-in-out both;
  box-shadow: 0 -2px 6px rgba(255, 255, 255, 0.3);
  backface-visibility: hidden;
}

.flip.down.go .back:after {
  animation: backFlipDown 0.6s ease-in-out both;
}

@keyframes frontFlipDown {
  0% {
    transform: perspective(160px) rotateX(0deg);
  }

  100% {
    transform: perspective(160px) rotateX(-180deg);
  }
}

@keyframes backFlipDown {
  0% {
    transform: perspective(160px) rotateX(180deg);
  }

  100% {
    transform: perspective(160px) rotateX(0deg);
  }
}

/** {*/
/*  outline: solid 1px red;*/
/*}*/
</style>
