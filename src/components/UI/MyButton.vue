<template>
  <button>
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button',
}
</script>

<style lang="scss" scoped>

button {
  color:#fff;
  background: transparent;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  border-radius: 5px;
  padding: 10px 25px;
  background-color: #89d8d3;
  background-image: linear-gradient(315deg, #89d8d3 0%, #03c8a8 74%);
  border: none;
  z-index: 1;

  &:after {
  position: absolute;
  content: "";
  width: 100%;
  height: 0;
  bottom: 0;
  left: 0;
  z-index: -1;
  border-radius: 5px;
  background-color: #4dccc6;
  background-image: linear-gradient(315deg, #4dccc6 0%, #96e4df 74%);
  transition: all 0.3s ease;
  }

  &:hover {
    color: #fff;

    &:after {
      top: 0;
      height: 100%;
    }
  }

  &:focus {
    outline-color: #03c8a8;
    color: #fff;

    &:after {
      top: 0;
      height: 100%;
    }
  }

  &:active {
      top: 2px;
  }
}



</style>