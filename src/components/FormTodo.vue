<template>
    <div class="form-todo form-group">
    <p>
        <input placeholder="Author" type="text" name="author" class="form-control" v-model="author" />
    </p>
    <p>
        <textarea placeholder="Comment" name="message"  class="form-control" v-model="message"></textarea>
    </p>
    <button @click="addComment" type="submit" class="btn btn-primary">Comment</button>
  </div>
</template>

<script>
export default {
    data() {
      return {
        name: '',
        message: ''
      }
    },
    methods: {
      addComment() {
        if (this.message.trim() === '') {
          return;
        }
        this.$emit('add-todo', {
          author: this.author,
          message: this.message,
        });
        this.author = '';
        this.message = '';
      }
    }
}
</script>

<style>

</style>