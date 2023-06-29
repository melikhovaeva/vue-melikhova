<template>
  <input :value="modelValue" @input="updateInput" class="add-comment__input" type="text">
</template>

<script>
export default {
  name: 'my-input',
  props: {
    modelValue: [String, Number]
  }, 
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style lang="scss" scoped>
.add-comment__input {
  margin-top: 0.5rem;
  border-radius: 1rem;
  border: 0;
  outline: 0;
  padding: 1rem;
  background-color: #EBECF0;
  text-shadow: 1px 1px 0 #FFF;
  box-shadow:  inset 2px 2px 5px #BABECC, inset -5px -5px 10px #FFF;

  &:focus {
    box-shadow:  inset 1px 1px 2px #BABECC, inset -1px -1px 2px #FFF;
  }
}
</style>