
<template>
  <!-- eslint-disable -->
  <div class="app">
    <PostForm @create="createPost" />
    <PostList v-bind:posts="posts" @clear="clearPosts" />
  </div>
</template>

<script>
import PostForm from "./components/PostForm";
import PostList from "./components/PostList";
export default {
  components: {
    PostList,
    PostForm,
  },
  data() {
    return {
      posts: [
        { id: 1, title: "Javascript 1", body: "Description 1" },
        { id: 2, title: "Javascript 2", body: "Description 1" },
        { id: 3, title: "Javascript 3", body: "Description 1" },
        { id: 4, title: "Javascript 4", body: "Description 1" },
      ],
    };
  },
  methods: {
    inputTitle(event) {
      this.title = event.target.value;
    },
    createPost(post) {
      this.posts.push(post);
    },
    clearPosts() {
      this.posts = [];
    }
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
</style>
