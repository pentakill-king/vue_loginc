<template>
  <div>
    <div
      class="ipt radius5"
      :class="{'is-err':error}"
    >
      <!-- 输入框 类型 值 提示 名字 方法-->
      <input
        :type="type"
        :value="value"
        :placeholder="placeholder"
        :name="name"
        @input="$emit('input',$event.target.value)"
      >
      <!-- 内按钮 隐藏 变灰 事件-->
      <button class="radius5"
        v-if="btnt"
        :disabled="disabled"
        @click="$emit('btnclick')"
      >{{btnt}}</button>

    </div>
    <!-- 错误提示框 -->
    <div
      v-if="error"
      class="ierr"
    >{{error}}</div>
  </div>
</template>

<script>
export default {
  props: {
    type: String,
    value: String,
    placeholder: String,
    name: String,
    btnt: String,
    disabled: Boolean,
    error: {}
  }
};
</script>

 <style lang="less" scoped>
 
.ipt {
  display: flex;
  width: 300px;
  height: 30px;
  border: 1px solid gray;
  margin: 1vh auto;

  input {
    border: none;
    width: 100%;
    font-size: 16px;
  }
  button {
    width: 110px;
    background-color: rgb(3, 109, 209);
    border: none;
    height: 100%;
    color: white;
  }
}

.ierr {
  color: red;
}
.is-err {
  border-color: red;
}
</style>