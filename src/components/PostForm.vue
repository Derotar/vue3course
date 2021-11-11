<template>
  <div>
    <form @submit.prevent>
      <h4>Create post</h4>
      <MyInput v-model="post.title" type="text" placeholder="title" />
      <MyInput v-model="post.body" type="text" placeholder="description" />
<<<<<<< HEAD
      <MyButton @click="createPost" style="align-self: flex-end; margin-top: 20px"
        >Create</MyButton
      >
=======
      <MyButton style="margin-top: 15px" @click="createPost">Create</MyButton>
>>>>>>> second
    </form>
  </div>
</template>

<script>
<<<<<<< HEAD
import MyInput from "../components/UI/MyInput.vue";
import MyButton from "../components/UI/MyButton.vue";
=======
import MyButton from "../components/UI/MyButton.vue";
import MyInput from "./UI/MyInput.vue";
>>>>>>> second
export default {
  components: {
    MyButton,
    MyInput,
  },
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
<<<<<<< HEAD
      if (!this.post.title) {
        this.post.title = "default title";
      }
      if (!this.post.body) {
        this.post.body = "default body";
      }
=======
      if (!this.post.title) this.post.title = "Egor";
      if (!this.post.body) this.post.body = "Nikolaev";
>>>>>>> second
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
<<<<<<< HEAD
</style>
=======
</style>
>>>>>>> second
