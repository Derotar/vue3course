
<template>
  <!-- eslint-disable -->
  <div class="app">
    <h1>Страница с постами</h1>
    <my-button v-show="false" @click="fetchPosts"> Get Posts </my-button>
    <my-button @click="showDialog" style="margin: 15px 0"
      >Создать пост</my-button
    >
    <input type="text" name="" id="" v-model.trim="modificatorValue">
    <my-dialog v-model:show="dialogVisible">
      <PostForm @create="createPost" />
    </my-dialog>

    <PostList v-bind:posts="posts" @clear="clearPosts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from "./components/PostForm";
import PostList from "./components/PostList";
import MyButton from "./components/UI/MyButton.vue";
import MyDialog from "./components/UI/MyDialog.vue";
import axios from 'axios';
export default {
  components: {
    PostList,
    PostForm,
    MyDialog,
    MyButton,
  },
  data() {
    return {
      posts: [

      ],
      dialogVisible: false,
      modificatorValue: '',
    };
  },
  methods: {
    inputTitle(event) {
      this.title = event.target.value;
    },
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    clearPosts() {
      this.posts = [];
    },
    removePost(post) {
      this.posts = this.posts.filter((res) => res.id != post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        const res = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
        this.posts = res.data;
      }catch(error){
        console.error(error);
      }
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
