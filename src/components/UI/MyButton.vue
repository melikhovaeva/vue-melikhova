<template>
  <button class="add-comment__button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button',
}
</script>

<style>
.add-comment__button {
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
  border-radius: 0.8rem;
  align-self: flex-end;
}
</style>