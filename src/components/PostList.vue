<template>
  <!-- eslint-disable -->
  <div>
    <button class="btn" @click="clearPosts"> Clear posts </button>
    <div class="post" v-for="post in posts">
      <div>
        Title: <strong> {{ post.title }} </strong>
      </div>
      <div>
        Description: <strong> {{ post.body }} </strong>
      </div>
    </div>
  </div>
</template>

<script>
export default {
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
        }
    }
};
</script>

<style scoped>
.post {
  padding: 15px;
  border: 3px solid teal;
  margin-top: 15px;
}
.btn {
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>