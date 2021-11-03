<template>
  <!-- eslint-disable -->
  <div v-if="posts.length > 0">
    <div><h3>Список пользователей</h3></div>
    <div>
      <button class="btn" @click="clearPosts">Clear posts</button>
      <PostItem
        :post="post"
        v-for="post in posts"
        :key="post.id"
        @remove="$emit('remove', post)"
      ></PostItem>
    </div>
  </div>
  <div v-else><h3>Список пользователей пуст</h3></div>
</template>

<script>
import PostItem from "../components/PostItem.vue";
export default {
  components: {
    PostItem,
  },
  data() {
    return {};
  },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
  methods: {
    clearPosts() {
      this.$emit("clear");
    },
  },
};
</script>

<style scoped>
.btn {
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>