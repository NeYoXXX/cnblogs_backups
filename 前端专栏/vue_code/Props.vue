<template>
  <div>
      type:{{type}}
      <br/>
      list:{{list}}
      <br/>
      isVisible:{{isVisible}}
      <br/>
      <button @click="handleClick">change type</button>
  </div>
</template>

<script>
export default {
    name:"Test",
    // 关闭原生属性自动挂载，比如title
    inheritAttrs:false,
    // 自定义属性
    props:{
        name:String,
        type:{
            validator:function(value){
                return ["success","warning","danger"].includes(value);
            }
        },
        list:{
            type:Array,
            default:()=>[]
        },
        isVisible:{
            type:Boolean,
            default:false
        },
        onChange:{
            type:Function,
            default:()=>{}
        }
    },
    methods: {
        handleClick(){
            // 不要这样做，报错，原因：属性是单项数据流，不能在组件中直接修改父组件传递的值。
            // this.type = "warning",

            // 可以，还可以更好
            this.onChange(this.type === "success" ? "warning" : "success")
        }
    },
}
</script>

<style>

</style>
