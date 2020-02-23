<template>
  <div class="ly-radio-group">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'ly-radio-group',
  provide () {
    return {
      RadioGroup: this
    }
  },
  props: {
    value: null
  }
}
</script>

<style>

</style>
