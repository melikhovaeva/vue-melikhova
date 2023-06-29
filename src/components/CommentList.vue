<template>
  <section class="comments">
    <div v-if="comments.length > 0" class="comments__wrapper">
      <h2 class="comments__title">Список комментариев</h2>
      <ul class="comments__list">
        <comment-item 
          @showDialog="changeParentCommentId"
          v-for="comment in reactionAndChildSum"
          :comment="comment"
          :key="comment.comment.id"
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
  },
  data() {
    return {
      commentList: this.comments,
    }
  },
  methods: {
    haveChild(parent, nest, arr1, arr2) {
      arr1.forEach((element) => {
        if (parent.id === element.parentId) {
          arr2.push({
            comment: element,
            nest: nest,
            reactionSum: 0,
            childs: 0,
          });
          this.haveChild(element, nest + 1, arr1, arr2);
        }
      });
    },
    changeParentCommentId(parentCommentId) {
      this.$emit('reply', parentCommentId);
    },
  },
  computed: {
    sortByNesting() {
      let sortedComments = [];
      this.commentList.forEach((comment) => {
        if (comment.parentId === null || !comment.parentId) {
          sortedComments.push({
            comment: comment,
            nest: 0,
            reactionSum: 0,
            childs: 0,
          });
          this.haveChild(comment, 1, this.commentList, sortedComments);
        }
      });
      return sortedComments;
    },
    reactionAndChildSum() {
      let arr = this.sortByNesting;
      for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
          const parrent = arr[i];
          const child = arr[j];
          if (parrent.comment.id === child.comment.parentId) {
            parrent.childs++;
            parrent.reactionSum += child.comment.reaction;
          }
        }
      }
      return arr;
    },
  },
}
</script>

<style lang="scss" scoped>
.comments {
  margin: 10px;
  display: flex;
  flex-direction: column;
}

.comments__wrapper {
  max-width: 100%;
}

.comments__list {
  list-style: none;
}

@media (min-width: 425px) {
  .comments__wrapper {
    min-width: 400px;
  }
}

@media (min-width: 768px) {
  .comments__wrapper {
    min-width: 700px;
  }
}

@media (min-width: 1024px) {
  .comments__wrapper {
    min-width: 1000px;
  }
}

@media (min-width: 1440px) {
  .comments__wrapper {
    min-width: 1400px;
  }
}

</style>