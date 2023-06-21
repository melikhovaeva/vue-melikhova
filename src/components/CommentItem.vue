<template>
  <li class="comments__comment comment">
    <p class="comment__author"> {{ comment.author }} </p>
    <p class="comment__description"> {{ comment.text }} </p>
  </li>
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
  word-break: break-word;
}

.comment__description {
  font-size: 1.3rem;
  margin-top: 1rem;
  word-break: break-word;
}

</style>