<template>
  <div>
    <h1>{{ msg }}</h1>
    <div class="flip down">
      <div class="digital front number0"></div>
      <div class="digital back number1"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FlipClock",
  props: {
    msg: String,
  },
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

/** {*/
/*  outline: solid 1px red;*/
/*}*/
</style>
