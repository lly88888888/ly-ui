<template>
  <div
    class="ly-switch"
    @click="handleClick"
    :class="{'is-checked':value}"
    >
    <span class="ly-switch__core" ref="core">
      <span class="ly-switch__button"></span>
    </span>
    <input type="checkbox" :name="name" class="ly-switch__input" ref="input">
  </div>
</template>

<script>
export default {
  name: 'ly-switch',
  props: {
    value: {
      type: Boolean,
      default: false
    },
    name: {
      type: String,
      default: ''
    },
    activeColor: {
      type: String,
      default: ''
    },
    inactiveColor: {
      type: String,
      default: ''
    }
  },
  methods: {
    async handleClick () {
      this.$emit('input', !this.value)
      await this.$nextTick()
      this.coreColor()
      this.$refs.input.checked = this.value
    },
    coreColor () {
      if (this.activeColor || this.inactiveColor) {
        const color = this.value ? this.activeColor : this.inactiveColor
        this.$refs.core.style.backgroundColor = color
        this.$refs.core.style.borderColor = color
      }
    }
  },
  mounted () {
    this.coreColor()
    this.$refs.input.checked = this.value
  }
}
</script>

<style lang="scss">
.ly-switch {
  display: inline-flex;
  align-items: center;
  position: relative;
  font-size: 14px;
  line-height: 20px;
  height: 20px;
  vertical-align: middle;

  .ly-switch__input {
    position: absolute;
    width: 0;
    height: 0;
    opacity: 0;
    margin: 0;
  }
  .ly-switch__core {
    margin: 0;
    display: inline-block;
    position: relative;
    width: 40px;
    height: 20px;
    border: 1px solid #dcdfe6;
    outline: none;
    border-radius: 10px;
    box-sizing: border-box;
    background: #dcdfe6;
    cursor: pointer;
    transition: border-color .3s,background-color .3s;
    vertical-align: middle;
    .ly-switch__button {
      position: absolute;
      top: 1px;
      left: 1px;
      border-radius: 100%;
      transition: all .3s;
      width: 16px;
      height: 16px;
      background-color: #fff;
    }
  }
}

.ly-switch.is-checked {
  .ly-switch__core {
    border-color: #409eff;
    background-color: #409eff;
    .ly-switch__button {
      transform: translateX(20px);
    }
  }
}
</style>
