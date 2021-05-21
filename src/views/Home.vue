<template>
  <div id="home">
    <h2>Home page</h2>
    <PostForm />
    <h2>{{postsCount}}</h2>
    <router-link to="/todos">Todos</router-link>
    <div class="post" v-for="post of validPosts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
import PostForm from "@/components/PostForm";
export default {
  name: "Home",
  components: {PostForm},
  // computed: {
  //   allPosts() {
  //     return this.$store.getters.allPosts
  //   }
  // },
  computed: mapGetters(["validPosts", "postsCount"]),

  async mounted() {
    // this.$store.dispatch('fetchPosts')
    await this.fetchPosts(5);
  },
  methods: mapActions(['fetchPosts']),
}
</script>

<style scoped>
  #home {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: 60px auto;
    width: 400px;
  }
  .post {
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-bottom: 1rem;
  }
</style>