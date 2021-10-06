<template>
  <div class="posts-show">
    <h4>{{ post.title }}</h4>
    <img :src="post.image" alt="" />
    <p>body: {{ post.body }}</p>
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
  methods: {},
};
</script>
