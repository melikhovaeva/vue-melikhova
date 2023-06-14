<template>
  <section class="comments">
    <div class="comments__wrapper">
      <h2 class="comments__title">Список комментариев</h2>
      <comment-item 
        v-for="comment in comments"
        :comment="comment" 
      />
    </div>
  </section>
</template>

<script>
import CommentItem from "./CommentItem.vue";
export default {
  components: {
    CommentItem,
  },
  props: {
    comments: {
      type: Array, 
      required: true,
    }
  }
}
</script>

<style scoped>
.comments {
  margin: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.comments__wrapper {
  min-width: 300px;
  max-width: 100%;
}
</style>