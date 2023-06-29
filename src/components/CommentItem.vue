<template>
  <li 
    class="comments__comment comment"
    :style="{
      'margin-left': nestMargin + 'px',
    }"
    :class="changeColorOnEvent"
  >
    <p class="comment__author"> {{ comment.comment.author }} </p>
    <p class="comment__description"> {{ comment.comment.text }} </p>
    <div class="comment__reply" 
      v-if="comment.childs">
      <p class="comment__reply-counter">{{ comment.childs }}</p>
      <svg class="comment__reply-icon" viewBox="0 0 100 100">
        	<path d="M99.3,19.5c-0.3-5.5-4.7-9.8-10-9.8H10.5C5,9.7,0.5,14.3,0.5,19.9v42.3c0,5.5,4.6,10.2,10.1,10.2h2.3v14.1
          c0,1.5,0.8,2.8,2.2,3.4c0.6,0.3,1.1,0.4,1.7,0.4c1,0,1.9-0.4,2.6-1.1l17.3-16.9h17.4c0.1,0.2,0.3,0.4,0.5,0.6
          C57.4,75.8,67,84.7,67.4,85c0.9,0.8,2.1,1.3,3.3,1.3c2.7,0,4.8-2.2,4.8-4.9v-2.9c8.9,0.6,13.5,3.4,13.8,4.5c0,1.8,1.4,3.2,3.2,3.3
          l0.1,0c1.8,0,3.3-1.5,3.3-3.3c0-0.2,0-0.3,0-0.5c-0.1-3.9-1.3-7.6-3.3-10.8c3.9-1.4,6.9-5.3,6.9-9.7V19.5H99.3z M73.1,73.5l-2.5,0
          v7.7c-1.2-1.1-6-5.5-9.4-8.8c-1.1-1-2-1.9-2.7-2.6c0.6-0.6,1.5-1.4,2.4-2.3c3.5-3.3,8.5-8,9.7-9.1v7.6l2.4,0.1
          c2.4,0.1,4.7,0.6,6.8,1.4c2.7,1.1,5.1,2.8,7,4.9c1.2,1.4,2.2,3,3,4.7C85.9,74.9,80,73.6,73.1,73.5z M94.3,62.2c0,2.8-2.3,5.2-5,5.2
          h-0.4c-3.5-3.3-8.2-5.6-13.4-6.2V58c0-2.7-2.2-4.9-4.8-4.9c-1.2,0-2.4,0.5-3.3,1.3c-0.4,0.4-10,9.2-12.8,12.1
          c-0.3,0.3-0.5,0.6-0.7,0.9H34.5L17.8,83.7V67.4h-7.3c-2.7,0-5.1-2.4-5.1-5.2V19.9c0-2.8,2.3-5.2,5.1-5.2h78.8c2.7,0,4.8,2.2,5,5
          V62.2z"/>
        <path d="M74.8,23.3H24.3c-1.4,0-2.5,1.1-2.5,2.5c0,1.4,1.1,2.5,2.5,2.5h50.5c1.4,0,2.5-1.1,2.5-2.5C77.3,24.4,76.3,23.3,74.8,23.3z
          "/>
        <path d="M74.8,32.8H24.3c-1.4,0-2.5,1.1-2.5,2.5c0,1.4,1.1,2.5,2.5,2.5h50.5c1.4,0,2.5-1.1,2.5-2.5C77.3,33.9,76.3,32.8,74.8,32.8z
          "/>
        <path d="M74.8,42.3H24.3c-1.4,0-2.5,1.1-2.5,2.5c0,1.4,1.1,2.5,2.5,2.5h50.5c1.4,0,2.5-1.1,2.5-2.5C77.3,43.4,76.3,42.3,74.8,42.3z
          "/>
        <path d="M54,51.8H24.3c-1.4,0-2.5,1.1-2.5,2.5c0,1.4,1.1,2.5,2.5,2.5H54c1.4,0,2.5-1.1,2.5-2.5C56.5,52.9,55.3,51.8,54,51.8z"/>
      </svg>
    </div>
    <my-button
      class="comment__button"
      @click="showDialog">
      Ответить
    </my-button>
  </li>
</template>

<script>
export default {
  props: {
    comment: {
      type: Object,
      required: true,
    }
  },
  methods: {
    showDialog() {
      this.$emit('showDialog', this.comment.comment.id);
    },
  },
  computed: {
    nestMargin() {
      return 25 * this.comment.nest;
    },
    changeColorOnEvent() {
      if (this.comment.reactionSum > 0) {
        return 'comment--green';
      } else if (this.comment.reactionSum < 0) {
        return 'comment--red';
      }
      return;
    },
  }
}
</script>

<style lang="scss">
.comment {
  display: flex;
  flex-direction: column;
  margin-top: 1rem;
  padding: 15px;
  border: 2px solid teal;
  border-radius: 1rem;

  &__author {
    font-size: 1.3rem;
    word-break: break-word;
  }

  &__description {
    font-size: 1.3rem;
    margin-top: 1rem;
    word-break: break-word;
  }

  &__reply {
    margin-top: 2rem;
    display: flex;
    align-items: center;
  }

  &__reply-icon {
    max-width: 30px;
  }

  &__reply-counter {
    margin-right: 0.5rem;
  }

  &--green {
    background-color: rgba(147, 255, 201, 0.322);
  }

  &--red {
    background-color: rgba(255, 196, 196, 0.322);
  }

  &__button {
    align-self: flex-end;
  }
}

</style>