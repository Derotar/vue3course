<template>
  <!-- eslint-disable -->
  <div class="app">
    <h1>Posts {{ selectedSort }}</h1>
    <MyInput v-model="searchQuery" placeholder="Search..." style="background: rgba(0, 112, 20, 0.1)"> </MyInput>
    <MySelect v-model="selectedSort" :options="sortOptions" />
    <MyButton @click="showDialog">Create post</MyButton>
    <MyDialog v-model:show="dialogVisible"> <PostForm @create="createPost" /></MyDialog>

    <PostList v-bind:posts="sortedAndSearchedPosts" @clear="clearPosts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from "./components/PostForm";
import PostList from "./components/PostList";
import MyButton from "./components/UI/MyButton.vue";
import MyDialog from "./components/UI/MyDialog.vue";
import axios from "axios";
import MySelect from "./components/UI/MySelect.vue";
import MyInput from './components/UI/MyInput.vue';
export default {
  components: {
    PostList,
    PostForm,
    MyDialog,
    MyButton,
    MySelect,
    MyInput,
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      selectedSort: "",
      sortOptions: [
        { value: "title", name: "By title" },
        { value: "body", name: "By description" },
      ],
      searchQuery : '',
      page: 1,
      limit: 10,
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
      this.posts = this.posts.filter((p) => p.id != post.id);
      console.log(this.posts);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        let res = (await axios.get("https://jsonplaceholder.typicode.com/posts", {
          params : {
            _page: this.page,
            _limit: this.limit,

          }
        })).data;
        this.posts = res;
      } catch (e) {
        console.error(e);
      }
    },
  },
  mounted() {
    this.fetchPosts();
  },
  computed: {
    sortedPosts() {
      return [...this.posts].sort((post1, post2) => {
        return post1[this.selectedSort]?.localeCompare(post2[this.selectedSort]);
      });
    },
    sortedAndSearchedPosts(){
      return this.sortedPosts.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()));
    }
  },
  // watch : {
  //   selectedSort(newValue) {
  //     this.posts.sort( (post1, post2) => {
  //       return post1[newValue]?.localeCompare(post2[newValue])
  //     })
  //   }
  // }
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
