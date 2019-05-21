<template>
  <div class="weui-slider-box">
    <div class="weui-slider">
      <div id="sliderInner" ref="linear" class="weui-slider__inner" @touchmove="touchmove" @touchend="touchend">
        <div id="sliderTrack" :style="{width: n+'%'}"  class="weui-slider__track"></div>
        <div id="sliderHandler" :style="{left:n+'%'}" @touchstart="touchstart" class="weui-slider__handler"></div>
      </div>
    </div>
    <div id="sliderValue" class="weui-slider-box__value" v-text="val"></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
        n:0,
        tmp:0,
        start:0,
        lenght:0,
    };
  },
  props: {
      value:{
          type:Number,
          default:0
      },
      max:{
        type:Number,
        default:100,
    }
  },
  computed:{
      val(){
          return Math.floor(this.n/this.max*100);
      }
  },
  methods: {
    //当按下手指时，触发ontouchstart。
    //当移动手指时，触发ontouchmove。
    //当移走手指时，触发ontouchend。
    touchstart(e){
      console.log(e.changedTouches[0].clientX);
      this.start=e.changedTouches[0].clientX;
      //vue里获取dom节点通过ref
      //获取线的总长度
      this.length=this.$refs['linear'].offsetWidth;
      // console.log(this.length);
      // this.length=this.$refs['linear'];
      // console.log(this.length);

    },
    touchmove(e){
      // console.log('move')；
      let x = e.changedTouches[0].clientX-this.start;
      this.n=this.tmp+(x/this.lenght*this.max);
      console.log(this.tmp);
      console.log(this.n);

    },
    touchend(e){
      console.log('canend');
      this.tmp = this.n;
  		this.$emit('input',this.n);
    }
    
  },
  watch: {
      value(val){
         this.n=val;
         this.tmp=val;

      }
     
  },
  created() {
      this.n = this.value;
      this.tmp = this.value;

  }
};
</script>
