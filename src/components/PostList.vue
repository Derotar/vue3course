<template>
  <!-- eslint-disable -->
  <div v-if="posts.length > 0">
    <MyButton style="margin-top: 15px" @click="clearPosts"> Clear posts </MyButton>
    <PostItem v-for="post in posts" :post="post" :key="post.id" @remove="removePost">
    </PostItem>
  </div>
  <div v-else>No posts yet</div>
</template>

<script>
import PostItem from "../components/PostItem.vue"
import MyButton from "../components/UI/MyButton.vue"
export default {
  components : {
    PostItem, MyButton,
  },
    data () {
        return {}
    },
    props : {
        posts: {
            type: Array,
            required: true,
        }
    },
    methods : {
        clearPosts(){
            this.$emit('clear');
        },
        removePost(post) {
          this.$emit('remove', post);
          console.log(`remove in list ${post}`);
        },
    }
};
</script>

<style scoped>

</style>