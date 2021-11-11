<template>
  <div>
    <form @submit.prevent>
      <h4>Create post</h4>
      <MyInput v-model="post.title" type="text" placeholder="title" />
      <MyInput v-model="post.body" type="text" placeholder="description" />
      <MyButton @click="createPost" style="align-self: flex-end; margin-top: 20px"
        >Create</MyButton
      >
    </form>
  </div>
</template>

<script>
import MyInput from "../components/UI/MyInput.vue";
import MyButton from "../components/UI/MyButton.vue";
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
      if (!this.post.title) {
        this.post.title = "default title";
      }
      if (!this.post.body) {
        this.post.body = "default body";
      }
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
  watch : {
    selectedSort(newValue) {
      console.log(newValue);
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>
