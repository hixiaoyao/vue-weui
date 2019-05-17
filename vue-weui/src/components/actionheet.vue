<template>
    <div>
        <div class="weui-mask" id="iosMask" v-show="show1"></div>
        <div class="weui-actionsheet" id="iosActionsheet">
            <div class="weui-actionsheet__title">
                <p class="weui-actionsheet__title-text">这是一个标题，可以为一行或者两行。</p>
            </div>
            <div class="weui-actionsheet__menu">
                <div class="weui-actionsheet__cell">示例菜单</div>
                <div class="weui-actionsheet__cell">示例菜单</div>
                <div class="weui-actionsheet__cell">示例菜单</div>
                <div class="weui-actionsheet__cell">示例菜单</div>
            </div>
            <div class="weui-actionsheet__action">
                <div class="weui-actionsheet__cell" id="iosActionsheetCancel">取消</div>
            </div>
        </div>
    </div>


</template>


<script>
export default {
    data(){
        return{
            show1:false
        };
    },
    props:{
        value:{
            type:Boolean,
            default:false
        },
        title:{
            type:String,
            default:""
        },
        acttion:{
            type:Array,
            default(){
                return[];
            },
        }
    },
    methods:{
       close(type="cancel"){
           if(type="cancel"){
               this.show1=false;
               this.$emit("input",false);
           }
           this.$emit("close",type);
       }
    },
    watch:{
         value(val){
            this.show1=val;
        }
    },
    created(){
        this.show1=this.value
    },
}
</script>



<style>




</style>
