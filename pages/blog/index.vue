<template>
  <div class="container mt-5">
    <h1>Blog</h1>
    <div class="card my-2"
      v-for="post in posts" :key="post.id"
    >
      <div class="card-body">
        <div class="card-title">
          <nuxt-link :to="`/blog/${post.id}`">
            <h1 v-text="post.title"></h1>
          </nuxt-link>
        </div>
        <div class="card-text">
          <p v-text="post.body"></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  export default {
    name: 'Blog',
    head: {
      title: 'Página de blogs'
    },
    /*
    data() {
      return {
        posts: [],
        valid: true,
        state: false,
      }
    }
    */
    data: () => (
      {
        posts: [],
      }
    ),
    methods: {
      async getPosts() {
        try {
          let allPosts = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=20');
          this.posts = Object.freeze(allPosts.data);
        } catch (error) {
          console.log('error:', error);
        }
      }
    },
    created() {
      this.getPosts();
    }
  }
</script>