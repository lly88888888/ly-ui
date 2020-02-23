<template>
  <div class="ly-form-item">
    <label class="ly-form-item__label" :style="{'width':Form.labelWidth}">{{label}}</label>
    <div class="ly-form-item__content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ly-form-item',
  props: {
    label: {
      type: String
    }
  },
  inject: {
    Form: {
      default: ''
    }
  },
  computed: {
    isForm () {
      return !!this.Form
    }
  }
}
</script>

<style lang="scss">
.ly-form-item {
  margin-bottom: 25px;
  .ly-form-item__label {
    text-align: right;
    vertical-align: middle;
    float: left;
    font-size: 14px;
    color: #606266;
    line-height: 40px;
    padding: 0 12px 0 0;
    box-sizing: border-box;
  }
  .hm-form-item__content{
    line-height: 40px;
    position: relative;
    font-size: 14px;
    overflow: hidden;
  }
}
</style>
