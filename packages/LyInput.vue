<template>
  <div class="ly-input" :class="{'ly-input--suffix':showSuffix}">
    <input
      class="ly-input__inner"
      :name="name"
      :type="showPassword ? (passwordVisible ? 'text': 'password'): type"
      :placeholder="placeholder"
      :disabled="disabled"
      :class="{'is-disabled':disabled }"
      :value="value"
      @input="input">
      <span class="ly-input__suffix" v-if="showSuffix">
        <i class="ly-icon-circle-close" v-if="clearable && value" @click="clearAble"></i>
        <i class="ly-icon-view" :class="{'ly-icon-view-active':passwordVisible}" v-if="showPassword" @click="handlePassword"></i>
      </span>
  </div>
</template>

<script>
export default {
  name: 'ly-input',
  props: {
    type: {
      type: String,
      default: 'text'
    },
    placeholder: {
      type: String,
      default: ''
    },
    disabled: {
      type: Boolean,
      default: false
    },
    name: {
      type: String,
      default: ''
    },
    value: {
      type: String,
      default: ''
    },
    clearable: {
      type: Boolean,
      default: false
    },
    showPassword: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      passwordVisible: false
    }
  },
  methods: {
    input (e) {
      this.$emit('input', e.target.value)
    },
    clearAble () {
      this.$emit('input', '')
    },
    handlePassword () {
      this.passwordVisible = !this.passwordVisible
    }
  },
  computed: {
    showSuffix () {
      return this.clearable || this.showPassword
    }
  }
}
</script>

<style lang="scss">
.ly-input {
  width: 180px;
  position: relative;
  font-size: 14px;
  display: inline-block;
  .ly-input__inner {
    cursor: pointer;
    -webkit-appearance: none;
    background-color: #fff;
    background-image: none;
    border-radius: 4px;
    border: 1px solid #dcdfe6;
    box-sizing: border-box;
    color: #000;
    display: inline-block;
    font-size: inherit;
    height: 40px;
    line-height: 40px;
    outline: none;
    padding: 0 15px;
    transition: border-color .2s cubic-bezier(.645,.045,.355,1);
    width: 100%;

    &:focus {
      outline: none;
      border-color: #409eff;
    }
    &.is-disabled {
      background-color: #f5f7fa;
      border-color: #e4e7ed;
      color: #c0c4cc;
      cursor: not-allowed;
    }
  }

}
.ly-input--suffix {
  .ly-input__inner {
    padding-right: 30px;
  }
  .ly-input__suffix {
    position: absolute;
    height: 100%;
    right: 10px;
    top: 0;
    line-height: 40px;
    text-align: center;
    color: #c0c4cc;
    transition: all .3s;
    z-index: 900;
    i {
      color: #c0c4cc;
      font-size: 14px;
      cursor: pointer;
      transition: color .2s cubic-bezier(.645,.045,.355,1);
    }
    .ly-icon-view-active{
      color: skyblue;
    }
  }
}
</style>
