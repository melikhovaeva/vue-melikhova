<template>
  <article class="comments__comment comment">
    <p class="comment__author"> {{ comment.author }} </p>
    <p class="comment__description"> {{ comment.description }} </p>
  </article>
</template>

<script>
export default {
  props: {
    comment: {
      type: Object,
      required: true,
    }
  }
}
</script>

<style>
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