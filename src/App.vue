<template>
  <div class="app__wrapper">
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
      v-if="!isCommentsLoading"
    />
    <p v-else>Идет загрузка...</p>
  </div>
</template>

<script>
import CommentForm from './components/CommentForm.vue';
import CommentList from './components/CommentList.vue';
import axios from 'axios';
import MyButton from './components/UI/MyButton.vue';

export default {
  components: { 
    CommentForm,
    CommentList,
    MyButton,
    
    },
  data() {
    return {
      comments: [],
      dialogVisible: false,
      isCommentsLoading: false,
    }
  },
  methods: {
    createComment(comment) {
      this.comments.push(comment);
      this.dialogVisible = false;
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchComments() {
     try { 
        this.isCommentsLoading = true;
        const response = await axios.get("http://194.67.93.117:80/comments");
        this.comments.length = 0; 
        this.comments.push(...response.data.reverse()); 
      } catch (e) { 
        alert("Ошибка"); 
      } finally {
        this.isCommentsLoading = false;
      }
    }, 
  },
   mounted() {
    this.fetchComments();
  }
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