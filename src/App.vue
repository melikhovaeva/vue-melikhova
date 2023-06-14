<template>
  <my-button
    @click="showDialog">
    Создать комментарий
  </my-button>
  <my-dialog v-model:show="dialogVisible"> 
    <comment-form
      @create="createComment"
    />
  </my-dialog>
  <comment-list 
    :comments="comments"
  />
</template>

<script>
import CommentForm from './components/CommentForm.vue';
import CommentList from './components/CommentList.vue';
import MyButton from './components/UI/MyButton.vue';
import MyDialog from './components/UI/MyDialog.vue';

export default {
  components: { 
    CommentForm, CommentList,
    MyDialog,
    MyButton
    },
  data() {
    return {
      comments: [
        // {id: 1, author: 'Eva', description: 'LaLala'},
        // {id: 2, author: 'Eva', description: 'LaLala 2'},
        // {id: 3, author: 'Eva', description: 'LaLala 3'}
      ],
      dialogVisible: false,
    }
  },
  methods: {
    createComment(comment) {
      this.comments.push(comment);
      this.dialogVisible = false;
    },
    showDialog() {
      this.dialogVisible = true;
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