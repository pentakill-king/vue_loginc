<template>
<div>
<div class="ipt" :class="{'is-err':error}">
    <!-- 输入框 类型 值 提示 名字 方法-->
    <input  :type="type"  :value="value" :placeholder="placeholder" :name="name" @input="$emit('input',$event.target.value)" >
    <!-- 内按钮 隐藏 变灰 事件-->
    <button v-if="btnt" :disabled="disabled" @click="$emit('btnclick')" >{{btnt}}</button>
    
    
</div>
<!-- 提示框 -->
<div v-if="error" class="ierr">{{error}}</div>
</div>
</template>

<script>
export default 
{
    props:{
        type:String,
        value:String,
        placeholder:String,
        name:String,
        btnt:String,
        disabled:Boolean,
        error:{}
    }
 }
</script>

 <style lang="less" scoped>
 .ipt{
     display: flex;
     width: 300px;
     height: 30px;
     border: 1px solid gray;

     input{
         border: none;
         width: 100%;
         font-size: 16px;
     }
     button{
         width: 110px;
         background-color: royalblue;
         border: none;
 }}

 .ierr{
     color: red;
 }
 .is-err{
     border-color: red;
 }
 </style>