<template>
  <div class="ly-checkbox-group">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'ly-checkbox-group',
  props: {
    value: {
      type: Array
    }
  },
  provide () {
    return {
      CheckboxGroup: this
    }
  }
}
</script>

<style>

</style>
