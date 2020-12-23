<template>
  <div>
    <input type="text" @input="onInput"/>
  </div>  
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
    onInput(e) {
      // Syntax is this.$emit(nameOfEventToEmit, valueToEmitWhenEventRuns)
      this.$emit('termChange', e.target.value);
    }

  }
}
</script>

<style lang="scss" scoped>
input {
  border: 1px solid #ccc;
}
</style>