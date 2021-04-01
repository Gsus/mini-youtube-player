<template>
  <div>
    <form @submit.prevent="onSubmit">
      <input type="text" placeholder="Search for videos..." v-model="inputText"/>
    </form>
  </div>  
</template>

<script>
export default {
  name: 'SearchBar',
  data() {
    return {
      inputText: '',
    }
  },
  methods: {
    onSubmit() {
      // Syntax is this.$emit(nameOfEventToEmit, valueToEmitWhenEventRuns)
      this.$emit('termChange', this.inputText);
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