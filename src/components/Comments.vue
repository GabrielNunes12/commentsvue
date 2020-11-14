<template>
  <div class="comentario">
    <div class="mainForm">
      <h1> Comments </h1>
      <hr>
      <FormTodo @add-todo="addComment"> </FormTodo>
      <br>
      <div class="showUpComments">
        <p v-if="comments.length <= 0"> No comments... </p>
        <div v-else class="showComments" v-for="(itemParaSerRenderizado, indexRender) in allComments" :key="indexRender">
          <span>Author: <strong> {{itemParaSerRenderizado.author}}</strong></span>
          <br/>
          <span>Message: <strong> {{itemParaSerRenderizado.message}}</strong></span>
          <div>
            <a href="#" @click.prevent="removeComment(indexRender)"> DELETE </a>
          </div>
          <div>
            <a href="#" @click.prevent="editComment"> EDIT </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FormTodo from './FormTodo'
export default {
  components: {
    FormTodo
  },
  data() {
    return {
      comments: []
    }
  },
  methods: {
    addComment(comment) {
      this.comments.push(comment)
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
    editComment() {
      localStorage.getItem(this.comments.map((showAllComments) => {
        return showAllComments;
      }))
    },
  },
  computed: {
    allComments(){
      return this.comments.map(comment => ({
        ...comment,
        author: comment.author.trim() === '' ? 'Annonymous' : comment.author
      }))
    }
  }
};
</script>
<style scoped>
.mainForm{
background-color: rgb(109, 109, 109);
padding: 10px 5px 10px 5px;
}
.showUpComments .showComments{
 padding: 10px 3px 4px 2px;
 border: 5px;
 border-radius: 5px;
}

</style>