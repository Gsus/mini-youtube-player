<template>
  <div>
    <input type="text" @input="onInput" placeholder="Search for videos..."/>
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
  width: 70%;
  max-width: 720px;
  margin: 2rem;
  border: none;
  border-radius: 0.6rem;
  padding: 0.85rem;
}
</style>