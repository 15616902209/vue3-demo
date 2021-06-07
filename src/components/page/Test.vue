<template>
  <div class="bgDiv">
  </div>
  <a href="#" class="button">
    <span>
       <h1 class="font"> 主题配色 </h1>
       <el-button @click="closeInterval()" style="background: rgba(0,0,0,0)">点击暂停</el-button>
       <el-button @click="initInterval()" style="background: rgba(0,0,0,0)">点击开始</el-button>
    </span>
  </a>
  <br/>
  <el-input type="textarea" placeholder="placeholder" v-model="model" style="width: 400px;">

  </el-input>
</template>

<script>
export default {
  data() {
    return {
      model: 0,
      red: 0,
      green: 0,
      blue: 0,
      transparent: 0,
      color: 'yellow',
      timeInterval: null,
      count: 0,
    }
  },
  created() {
    this.initInterval();
  },
  methods: {
    changeColor() {
      this.count++;
      //动态随机颜色
      this.red = Math.floor(Math.random() * 256);
      this.green = Math.floor(Math.random() * 256);
      this.blue = Math.floor(Math.random() * 256);
      this.transparent = Math.floor(Math.random() * 256);

      this.model = "红(R):" + this.red + ",绿(G):" + this.green + ",蓝(B):" + this.blue + ",透明度(O):" + this.transparent;

      //console.log(this.count);
      if (this.count === 100) {
        this.closeInterval();
        this.count = 0;
      }
    },
    initInterval() {
      //开始前先清除以前的定时器
      this.closeInterval();
      //定时器
      this.timeInterval = setInterval(this.changeColor, 2000);
    },
    closeInterval() {
      //清除定时器
      clearInterval(this.timeInterval);
    },
  }
}
</script>

<style>
.font {
  color: rgba(v-bind(red), v-bind(blue), v-bind(green), v-bind(transparent))
}

.bgDiv {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 900px;
  z-index: -999;
  background-image: linear-gradient(
      90deg,
      rgba(v-bind(green), v-bind(red), v-bind(blue), 0.7),
      rgba(v-bind(blue), v-bind(red), v-bind(green), 0.5),
      rgba(v-bind(red), v-bind(green), v-bind(blue), v-bind(transparent))
  );
}

.button {
  /*background-image: linear-gradient(90deg, #00C0FF 0%, #FFCF00 49%, #FC4F4F 100%);*/
  background-image: linear-gradient(
      90deg,
      rgba(v-bind(red), v-bind(green), v-bind(blue), v-bind(transparent)),
      rgba(v-bind(green), v-bind(red), v-bind(blue), 0.5),
      rgba(v-bind(blue), v-bind(red), v-bind(green), 0.7)
  );
  display: inline-block;
  padding: 3px;
  border-radius: 7px;
  text-decoration: none;
  position: relative;
  font-weight: 800;
  text-transform: uppercase;
}

.button span {
  display: inline-block;
  /*background: #191919;*/
  color: white;
  padding: 2rem 5rem;
  border-radius: 5px;
  font-size: 3rem;
}
</style>
