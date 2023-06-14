<template>
  <section class="add-comment">
    <div class="add-comment__wrapper">
      <h2 class="add-comment__title">Создание поста</h2>
      <form class="add-comment__form" @submit.prevent>
        <label class="add-comment__label">
          Автор: 
          <my-input 
            v-model="comment.author" 
            name="author" 
            type="text" 
            placeholder="Enter your name..." 
            required>
          </my-input>
        </label>
        <label class="add-comment__label">
          Комментарий: 
          <my-input
            v-model="comment.description" 
            name="comment"
            type="text" 
            placeholder="Enter your text..." 
            required>
          </my-input>
        </label>
        <my-button
          @click="createComment"
          class="add-comment__button">
          Создать
        </my-button>
      </form>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      comment: {
        author: '',
        description: '',
      }
    }
  },
  methods: {
    createComment() {
      this.comment.id = Date.now();
      this.$emit('create', this.comment)
      this.comment = {
        author: '',
        description: '',
      }
    }
  }
}
</script>

<style scoped>
.add-comment {
  margin: 20px;
}

.add-comment__wrapper {
  max-width: 100%;
}

.add-comment__form {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.add-comment__label {
  width: 100%;
  margin-top: 0.8rem;
  display: flex;
  flex-direction: column;
}

</style>