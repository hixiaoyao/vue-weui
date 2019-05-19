<template>
  <div class="weui-slider-box">
    <div class="weui-slider">
      <div id="sliderInner" class="weui-slider__inner">
        <div id="sliderTrack" :style="{width: n+'%'}"  class="weui-slider__track"></div>
        <div id="sliderHandler" :style="{left:n+'%'}" @click="mousedown" class="weui-slider__handler"></div>
      </div>
    </div>
    <div id="sliderValue" class="weui-slider-box__value" v-text="n"></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
        n:0,
    };
  },
  props: {
      value:{
          type:Number,
          default:50
      }
  },
  methods: {
    
    mousedown(e){
       var n = parseInt(this.n);
      var disX = e.clientX;
      document.onmousemove = function(e){
        this.n = e.clientX - disX + n;

      };
      document.onmouseup = function() {
        document.onmousemove = document.onmouseup = null;
      };
    }
  },
  watch: {
      value(val){
         this.n=val;
      }
     
  },
  created() {
      this.n = this.value;
  }
};
</script>
