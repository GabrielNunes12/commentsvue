<template>
  <div class="comentario">
    <div class="">
      <h1> Comments </h1>
      <hr>
      <p> 
        <input type="text" v-model="author" placeholder="author" />
      </p> 
      <br/>
      <p> 
        <input type="text" v-model="message" placeholder="message"/>
      </p>
      <br/>
      <button type="submit" @click="addComment">Comment</button>
      <div v-for="(itemParaSerRenderizado, indexRender) in allComments" :key="indexRender">
        <span>Author: <strong> {{itemParaSerRenderizado.author}}</strong></span>
        <br/>
        <span>Message: <strong> {{itemParaSerRenderizado.message}}</strong></span>
        <div>
          <a href="#" @click.prevent="removeComment(indexRender)"> DELETE </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Comment',
  
  data() {
    return {
      comments: [],
      author: '',
      message: ''
    }
  },
  methods: {
    addComment() {
      if(this.message.trim() === ''){
        return;
      }
      this.comments.push({
        author: this.author,
        message: this.message
      });
      this.author = '',
      this.message = ''
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
  computed: {
    allComments(){
      return this.comments.map(comment => ({
        ...comment,
        name: comment.author.trim() === '' ? 'Annonymous' : comment.author
      }))
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
