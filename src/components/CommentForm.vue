<template>
  <section class="add-comment">
    <div class="add-comment__wrapper">
      <h2 class="add-comment__title">Создание поста</h2>
      <form class="add-comment__form" @submit.prevent>
        <label class="add-comment__label">
          Автор: 
          <input 
            v-model="comment.author"
            class="add-comment__input" 
            type="text" 
            name="author" 
            placeholder="Enter your name..." 
            required>
        </label>
        <label class="add-comment__label">
          Комментарий: 
          <input
            v-model="comment.description"
            class="add-comment__input" 
            type="text" 
            name="comment" 
            placeholder="Enter your text..." 
            required>
        </label>
        <button
          @click="createComment"
          class="add-comment__button">
          Создать
        </button>
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

.add-comment__input {
  margin-top: 0.5rem;
  padding: 1rem;
  border-radius: 1rem;
   border: 1px solid teal;
}

.add-comment__button {
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
  border-radius: 0.8rem;
  align-self: flex-end;
}
</style>