<template>
  <div class="container">
    <div class="card">
      <div class="card-body">
        <div class="card-title">
          <h1 v-text="post.title"></h1>
        </div>
        <p><small v-text="post.authorName"></small></p>
        <div class="card-text">
          <p class="small" v-text="post.body"></p>
          <hr>
          <nuxt-link :to="{name: 'blog'}" class="btn btn-primary btn-sm">Prev</nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  export default {
    // data: () => (
    //   { 
    //     post: {},
    //   }
    // ),
    // asyncData({ app, store, route, params, query, env, isDev, isHMR, redirect, error })
    async asyncData({ params, error }) {
      try {
        // Post
        let URLPost = `https://jsonplaceholder.typicode.com/posts/${params.id}`;
        let postData = await axios.get(URLPost);
        let post = postData.data;
        // User data
        let URLUser = `https://jsonplaceholder.typicode.com/users/${postData.data.userId}`;
        let authorData = await axios.get(URLUser);
        post.authorName = authorData.data.name;
        return { post };
      } catch (error) {
        return { error };
      }
    }
  }
</script>