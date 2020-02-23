<template>
  <div id="app">
    <ly-button type="primary">按钮</ly-button>
    <ly-input type='password' show-password placeholder="请输入密码" v-model="password"></ly-input>
  </div>
</template>
<script>
export default {
  data () {
    return {
      password: ''
    }
  }
}
</script>
