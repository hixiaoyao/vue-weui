<template>
  <a href="javascript:;" @click="$emit('click')" class="weui-btn" :class="[typeStyle,disabledStyle,sizeStyle,loadingStyle]" >
    <i class="weui-loading" v-if="loading"></i>
    <slot></slot>
  </a>
</template>

<script>
export default {
  props: {
    //   负责样式
    type: {
      type: String,
      default: "default"
    },
    // 负责禁用/启用
    disabled:{
        type:Boolean,
        default:false
    },
    // 线框
    plain:{
        type:Boolean,
        default:false
    },
    // 按钮大小
    size:{
        type:String,
        default:'default'
    },
    loading:{
        type:Boolean,
        default:false
    }
  },
  computed: {
    typeStyle() {
      let s = "";
      switch (this.type) {
        case "primary":
          s = this.plain? "weui-btn_plain-primary":"weui-btn_primary";
          break;
        case "warning":
          s =  "weui-btn_warn";
          break;
        default:
          s =  this.plain? "weui-btn_plain-default":"weui-btn_default";
          break;
      }
      return s;
    },
    disabledStyle(){
        return this.disabled?'weui-btn_disabled ':'';
    },
    sizeStyle(){
        let s = '';
        switch(this.size){
            case 'mini':s='weui-btn_mini';break;
            case 'large':s='weui-btn_block';break;
            default:s='';break;
        }
        return s;
    },
    loadingStyle:function(){
        return this.loading?'weui-btn_loading':'';
    }
  }
};
</script>

<style>
</style>