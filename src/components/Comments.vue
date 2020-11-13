<template>
  <div class="comentario">
    <div class="">
      <h1> Comments </h1>
      <hr>
      <FormTodo @add-todo="addComment"> </FormTodo>
      <br>
      <div class="list-group">
        <p v-if="comments.length <= 0"> No comments... </p>
        <div v-else class="list-group-item" v-for="(itemParaSerRenderizado, indexRender) in allComments" :key="indexRender">
          <span>Author: <strong> {{itemParaSerRenderizado.author}}</strong></span>
          <br/>
          <span>Message: <strong> {{itemParaSerRenderizado.message}}</strong></span>
          <div>
            <a href="#" @click.prevent="removeComment(indexRender)"> DELETE </a>
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
      this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1);
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
