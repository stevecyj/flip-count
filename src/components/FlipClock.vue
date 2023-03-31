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
}
</style>
