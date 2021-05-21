<template>
  <form @submit.prevent="submit">
    <input type="text" placeholder="Title" v-model="title">
    <input type="text" placeholder="Body" v-model="body">
    <button type="submit">Create post</button>
    <hr>
  </form>
</template>

<script>
import {mapMutations} from 'vuex';
export default {
name: "PostForm",
  data() {
    return {
      title: "",
      body: ""
    };
  },
  methods: {
    ...mapMutations(['createPosts']),
    submit() {
      this.createPosts({
        title: this.title,
        body: this.body,
        id: Date.now()
      })
      this.title = this.body = ''
    }
  }
}
</script>

<style scoped>
  input {
    display: block;
    width: 100%;
    border: 1px solid #ccc;
    border-radius: 2px;
    padding: 10px;
    margin-bottom: 10px;
  }

</style>