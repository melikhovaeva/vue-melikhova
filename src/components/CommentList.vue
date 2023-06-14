<template>
  <section class="comments">
    <div class="comments__wrapper">
      <article class="comments__comment comment" v-for="comment in comments">
        <p class="comment__author"> {{ comment.author }} </p>
        <p class="comment__description"> {{ comment.description }} </p>
      </article>
    </div>
  </section>
</template>

<script>
export default {
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

.comment {
  margin-top: 1rem;
  padding: 15px;
  border: 2px solid teal;
  border-radius: 1rem;
}

.comment__author {
  font-size: 1.3rem;
}

.comment__description {
  font-size: 1.3rem;
  margin-top: 1rem;
}

</style>