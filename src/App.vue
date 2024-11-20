<script>

import axios from 'axios';

export default {
  data() {
    return {
      postsList: [],
      apiUrl: 'http://127.0.0.1:8000/api/posts',
    }
  },
  methods: {
    getPosts() {
      axios.get(this.apiUrl)
        .then((response) => {
          // handle success
          console.log(response);
          this.postsList = response.data.result;
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        })
        .finally(function () {
          // always executed
        });
    }
  },
  created() {
    this.getPosts();
  }
}
</script>

<template>
  <section>
    <h1 class="fw-bold text-center">Posts</h1>
    <ul>
      <li class="mb-3" v-for="post in postsList">
        {{ post.id }} -- {{ post.content }}

      </li>
    </ul>
  </section>
</template>

<style lang="scss">
@use "bootstrap/scss/bootstrap.scss" as *;
</style>
