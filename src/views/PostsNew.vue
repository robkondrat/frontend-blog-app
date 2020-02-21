<template>
  <div class="posts-new">
    <form v-on:submit.prevent="createPost()">
      <h1>New Post</h1>

      <ul>
        <li v-for="error in errors">{{ error }}</li>
      </ul>

      <div>
        Title: <input type="text" v-model="title">
      </div>
      <div>
        Body: <input type="text" v-model="body">
      </div>
      <div>
        Image: <input type="text" v-model="image">
      </div>

      <input type="submit" value="Create">
    </form>
  </div>
</template>

<style></style>


<script>
var axios = require("axios");

  export default {
    data: function() {
      return {
        title: "",
        body: "",
        image: "",
        errors: []
      };
    },
    created: function() {},
    methods: {
      createPost: function() {
        var clientParams = {
          title: this.title,
          body: this.body,
          image: this.image
        };

        axios
        .post("/api/posts", clientParams)
        .then(response => {
          this.$router.push("/posts");
        }).catch(error => {
          this.errors = error.response.data.errors;
        });
      }
    }
  };
</script>