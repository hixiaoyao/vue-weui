<template>
   <div :style="{opacity:show?1:0,display: show?'block':'none'}">
    <div class="weui-mask" @click="hide"></div>
    <div class="weui-dialog">
      <div class="weui-dialog__hd">
        <strong class="weui-dialog__title" v-text="title"></strong>
      </div>
      <div class="weui-dialog__bd">
          <slot></slot>
      </div>
      <div class="weui-dialog__ft">
        <a href="javascript:;" class="weui-dialog__btn weui-dialog__btn_default" @click="hide">取消</a>
        <a href="javascript:;" class="weui-dialog__btn weui-dialog__btn_primary" @click="confirm">确定</a>
      </div>
    </div>
  </div>  




</template>

<script>
export default {
    data(){
        return{
            show:false,
        };
    },
    props:{
        value:{
            type:Boolean,
            default:false
        },
        title:{
            type:String,
            default:''
        }

    },
    methods:{
        hide(){
            this.show = false;
            this.$emit("input",false); 
        },
        confirm(){
            this.$emit("confirm");
        }
    },
    watch:{
        value(val){
            this.show=val;
        },
    },
    created(){
        this.show=this.value;
    },
}
</script>
<style>

</style>
