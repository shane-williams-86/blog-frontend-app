<template>
  <div class="posts-index">
    <h1>All Posts</h1>
    <div v-for="post in posts" v-bind:key="post.id">
      <h4>{{ post.title }}</h4>
      <img :src="post.image" alt="" />
      <p>body: {{ post.body }}</p>
      <router-link :to="`/posts/${post.id}`">See Details</router-link>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      posts: [],
    };
  },
  created: function () {
    axios.get("/posts").then((response) => {
      console.log(response.data);
      this.posts = response.data;
    });
  },
  methods: {},
};
</script>
