<template>
  <section class="comments">
    <div v-if="comments.length > 0" class="comments__wrapper">
      <h2 class="comments__title">Список комментариев</h2>
      <ul class="comments__list">
        <comment-item 
          v-for="comment in comments"
          :comment="comment"
          :key="comment.id" 
        />
      </ul>
    </div>
    <h2 v-else class="comments__title">Комментариев нет</h2>
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
}

.comments__wrapper {
  min-width: 300px;
  max-width: 100%;
}

.comments__list {
  list-style: none;
}
</style>