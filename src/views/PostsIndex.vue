<template>
  <div class="posts-index">
    <h1>RoBz BlOgZ</h1>

    <div v-for="post in posts">
      <h2>{{ post.title }}</h2>
      <img v-bind:src="post.image" v-bind:alt="post.title">
      <p>{{ post.body }}</p>
      <br>
    </div>
  </div>
</template>

<style>
</style>

<script>
  var axios = require("axios");

  export default {
    data: function() {
      return {
        posts: []
      };
    },
    created: function() {
      axios
        .get("/api/posts")
        .then(response => {
          this.posts = response.data;
        });
      },
      methods: {}
    
  };
</script>