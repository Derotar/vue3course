<template>
  <div>
    <form @submit.prevent>
      <h4>Create post</h4>
      <MyInput v-model="post.title" type="text" placeholder="title" />
      <MyInput v-model="post.body" type="text" placeholder="description" />
      <MyButton style="margin-top: 15px" @click="createPost">Create</MyButton>
    </form>
  </div>
</template>

<script>
import MyButton from "../components/UI/MyButton.vue";
import MyInput from "./UI/MyInput.vue";
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
      if (!this.post.title) this.post.title = "Egor";
      if (!this.post.body) this.post.body = "Nikolaev";
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
</style>
