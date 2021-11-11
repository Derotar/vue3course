<template>
  <div v-if="posts.length > 0">
    <MyButton style="margin-top: 15px" @click="clearPosts"> Clear posts </MyButton>
    <transition-group name="post-list"> <PostItem v-for="post in posts" :post="post" :key="post.id" @remove="removePost"> </PostItem></transition-group>
  </div>
  <div v-else>No posts yet</div>
</template>

<script>
import PostItem from "../components/PostItem.vue";
import MyButton from "../components/UI/MyButton.vue";
export default {
  components: {
    PostItem,
    MyButton,
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
    removePost(post) {
      this.$emit("remove", post);
      console.log(`remove in list ${post}`);
    },
  },
};
</script>

<style scoped>
.post-list-item {
  display: inline-block;
  margin-right: 10px;
}
.post-list-enter-active,
.post-list-leave-active {
  transition: all 1s ease;
}
.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateX(130px) rotate(-34deg);
  /* transform: rotate(34deg) */
}


</style>
