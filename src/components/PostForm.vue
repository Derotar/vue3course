<template>
  <div>
    <form @submit.prevent>
      <h4>Create post</h4>
      <input
        class="input"
        v-model="post.title"
        type="text"
        placeholder="title"
      />
      <input
        class="input"
        v-model="post.body"
        type="text"
        placeholder="description"
      />
      <button class="btn" @click="createPost">Create</button>
    </form>
  </div>
</template>

<script>
export default {
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

.input {
  width: 100%;
  border: 3px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}
.btn {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>