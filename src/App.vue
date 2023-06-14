<template>
  <comment-form
    @create="createComment"
  />
  <comment-list 
    :comments="comments"
  />
</template>

<script>
import CommentForm from './components/CommentForm.vue';
import CommentList from './components/CommentList.vue';

export default {
  components: { 
    CommentForm, CommentList 
    },
  data() {
    return {
      comments: [
        {id: 1, author: 'Eva', description: 'LaLala'},
        {id: 2, author: 'Eva', description: 'LaLala 2'},
        {id: 3, author: 'Eva', description: 'LaLala 3'}
      ],
      author: '',
      description: '',
    }
  },
  methods: {
    createComment(comment) {
      this.comments.push(comment);
    }
  },
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-size: 20px;
  margin: 0 auto;
}

</style>