<template>
  <div class="app__wrapper">
    <my-button
      class="app__button"
      @click="showDialog">
      Создать комментарий
    </my-button>
    <my-dialog v-model:show="dialogVisible"> 
      <comment-form
        @create="postComments"
        :parentCommentId="parentCommentId"
      />
    </my-dialog>
    <comment-list 
      :comments="comments"
      v-if="!isCommentsLoading"
      @reply="showReplyDialog"
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
      parentCommentId: null,
      comments: [],
      dialogVisible: false,
      isCommentsLoading: false,
      evtSource: new EventSource('http://194.67.93.117:80/comments/stream'),
    }
  },
  methods: {
    createComment(comment) {
      this.comments.push(JSON.parse(comment.data));
      this.dialogVisible = false;
    },
    showReplyDialog(parentCommentId) {
      this.parentCommentId = parentCommentId;
      this.dialogVisible = true;
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
        console.log(error);
      } finally {
        this.isCommentsLoading = false;
      }
    }, 
    async postComments(comment) {
      try {
        let url = 'http://194.67.93.117:80/comments';
        let commentbody = {
          author: comment.author,
          text: comment.text,
          reaction: comment.reaction,
          parentId: comment.parentId,
        };

        const response = await axios.post(url, commentbody, {
          headers: {
            'Content-Type': 'application/json',
            Username: 'melikhovaeva',
          },
        });

        console.log(response.data);
        this.dialogVisible = false;
        this.parentCommentId = null;
      } catch (error) {
        alert(error);
      }
    },
    ourEventSource() {
      this.evtSource.onmessage = this.createComment;
    },
  },
   mounted() {
    this.fetchComments();
  },
  beforeMount(){
    this.fetchComments();
  },
  mounted() {
    this.ourEventSource();
  },
}
</script>

<style lang="scss">

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-size: 20px;
  margin: 0 auto;
}

.app__wrapper {
  margin: 1rem auto;
  width: 90%;
  max-width: 1440px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.app__button {
  align-self: flex-start;
}

</style>