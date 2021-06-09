<template>
  <div class="bgDiv">
  </div>
  <h3 class="font-color1"> 主题配色 </h3>
  <span class="font-color2">暂停后可用取色器获取喜欢的颜色</span>
  <hr/>
  <el-button @click="closeInterval()" style="background: rgba(0,0,0,0)">点击暂停</el-button>
  <el-button @click="initInterval()" style="background: rgba(0,0,0,0)">点击开始</el-button>
  <br/>
  <br/>


  <el-button class="colorButton">
  </el-button>

  <el-button class="colorButton">
  </el-button>


  <br/>
  <el-input type="textarea" placeholder="placeholder" v-model="model" style=" width: 400px;">

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
      this.transparent = Math.random();

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
      this.timeInterval = setInterval(this.changeColor, 1000);
    },
    closeInterval() {
      //清除定时器
      clearInterval(this.timeInterval);
    },
  }
}
</script>

<style>

.font-color1 {
  color: rgba(v-bind(red), v-bind(blue), v-bind(green), v-bind(transparent))
}

.font-color2 {
  color: rgba(v-bind(blue), v-bind(red), v-bind(green), v-bind(transparent))
}


.colorButton{
  background-image: linear-gradient(
      90deg,
      rgba(v-bind(red), v-bind(green), v-bind(blue), v-bind(transparent)),
      rgba(v-bind(green), v-bind(red), v-bind(blue), 0.5),
      rgba(v-bind(blue), v-bind(red), v-bind(green), 0.7)
  );
  width: 300px;
  height: 120px;
  border: 0px;
  border-radius: 7px;
}

.bgDiv {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 1080px;
  z-index: -999;
  background-image: linear-gradient(
      90deg,
      rgba(v-bind(green), v-bind(red), v-bind(blue), 0.7),
      rgba(v-bind(blue), v-bind(red), v-bind(green), 0.5),
      rgba(v-bind(red), v-bind(green), v-bind(blue), v-bind(transparent))
  );
}
</style>
