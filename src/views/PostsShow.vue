<template>
  <div class="posts-show">
    <h4>{{ post.title }}</h4>
    <img :src="post.image" alt="" />
    <p>body: {{ post.body }}</p>
    <router-link :to="`/posts/${post.id}/edit`">Edit</router-link>
    <button v-on:click="destroyPost">Delete</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      post: [],
    };
  },
  created: function () {
    axios.get(`/posts/${this.$route.params.id}`).then((response) => {
      console.log(response.data);
      this.post = response.data;
    });
  },
  methods: {
    destroyPost: function () {
      if (confirm("Are you sure you want to delete this recipe?")) {
        axios.delete(`/posts/${this.post.id}`).then((response) => {
          console.log(response.data);
          this.$router.push("/posts");
        });
      }
    },
  },
};
</script>
