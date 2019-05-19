<template>
  <div class="home">
    <h1>Hello</h1>

    <!-- 主题样式 -->
    <we-button type="primary">按钮</we-button>
    <we-button type="warning">按钮</we-button>
    <we-button type="default" disabled>按钮</we-button>
    <!-- 线框 -->
    <we-button type="primary" plain>按钮</we-button>
    <we-button type="warning" plain>按钮</we-button>
    <we-button type="default" plain disabled>按钮</we-button>
    <we-button type="default" disabled>按钮</we-button>
    <!-- 控制大小 -->
    <we-button type="primary" size="large">按钮</we-button>
    <we-button type="primary" size="default">按钮</we-button>
    <we-button type="primary" size="mini">按钮</we-button>

    <!-- loading -->
    <we-button type="primary" loading>按钮</we-button>
    <we-button @click="showDialog">显示：{{show}}</we-button>
    <we-dialog v-model="show" title="标题">插槽中的内容</we-dialog>

    <we-button @click="showActionShert">显示1：{{show1}}</we-button>
    <we-action-sheet v-model="show1" :action="['示例菜单1','示例菜单2','示例菜单3','示例菜单4',]"></we-action-sheet>

    <we-slide v-model="score"></we-slide>

    <br>
    <br>
    <br>
    <br>
    <br>
    <slider :min="0" :max="100" v-model="per"></slider>
    <br>
    <br>
    <br>
    <br>
    <br>
  </div>
</template>


<script>
// @ is an alias to /src
// 模块化引入这个按钮组件
import WeButton from "../components/button";
import WeDialog from "../components/dialog";
import WeActionSheet from "../components/actionheet";
import WeSlide from "../components/slide";
import slider from "../components/slider";

export default {
  name: "home",
  data() {
    return {
      show: false,
      show1: false,
      score: 10,
      per: 0
    };
  },
  methods: {
    showDialog() {
      console.log("show");
      this.show = true;
    },
    showActionShert() {
      console.log("show1");
      this.show1 = true;
    }
  },
  //注册组件，局部注册
  components: {
    WeButton,
    WeDialog,
    WeActionSheet,
    WeSlide,
    slider
  }
};
</script>
