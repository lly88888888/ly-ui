<template>
  <label class="ly-radio" :class="{'is-checked':label==model}">
    <span class="ly-radio__input">
      <span class="ly-radio__inner">
        <i></i>
      </span>
      <input type="radio" class="ly-radio__original" :name="name" :value="label" v-model="model">
    </span>
  <span class="ly-radio__label">
    <slot></slot>
    <template v-if="!$slots.default">
      label
    </template>
  </span>
  </label>
</template>

<script>
export default {
  name: 'ly-radio',
  props: {
    value: null,
    label: {
      type: [String, Number, Boolean],
      default: ''
    },
    name: {
      type: String,
      default: ''
    }
  },
  created () {
    console.log(this.RadioGroup)
  },
  computed: {
    model: {
      get () {
        return this.isGroup ? this.RadioGroup.value : this.value
      },
      set (value) {
        this.$emit('input', value)
        this.isGroup ? this.RadioGroup.$emit('input', value) : this.$emit('input', value)
      }
    },
    isGroup () {
      return !!this.RadioGroup
    }
  },
  inject: {
    RadioGroup: {
      default: ''
    }
  }
}
</script>

<style lang="scss">
.ly-radio {
  color: #606266;
  font-weight: 500;
  line-height: 1;
  position: relative;
  cursor: pointer;
  display: inline-block;
  white-space: nowrap;
  outline: none;
  font-size: 14px;
  margin-right: 30px;
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
  .ly-radio__input {
    white-space: nowrap;
    cursor: pointer;
    outline: none;
    display: inline-block;
    line-height: 1;
    position: relative;
    vertical-align: middle;
    .ly-radio__inner {
      border: 1px solid #dcdfe6;
      border-radius: 100%;
      width: 14px;
      height: 14px;
      background-color: #fff;
      position: relative;
      cursor: pointer;
      display: inline-block;
      box-sizing: border-box;
    }
    .ly-radio__original {
      opacity: 0;
      outline: none;
      position: absolute;
      z-index: -1;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      margin: 0;
    }
  }
  .ly-radio__label {
    font-size: 14px;
    padding-left: 10px;
  }
}
.ly-radio.is-checked {
  .ly-radio__input {
    .ly-radio__inner {
      border-color: #409eff;
      background: #409eff;
      i {
        width: 5px;
        height: 5px;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        background-color: #fff;
        border-radius: 50%;
      }
    }
  }
  .ly-radio__label {
    color:#409eff;
  }
}
</style>
