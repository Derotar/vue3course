<template>
  <!-- eslint-disable -->

  <div class="post">
    <div>
      <div>
        Title: <strong> {{ post.title }} </strong>
      </div>
      <div>
        Description: <strong> {{ post.body }} </strong>
      </div>
    </div>
    <div class="post__btns">
      <MyButton
      @click="$emit('remove', post)">Delete</MyButton>
    </div>
  </div>
</template>

<script>
import MyButton from "../components/UI/MyButton.vue"
export default {
    components : {
        MyButton,
    },
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.post {
  padding: 15px;
  border: 3px solid teal;
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

</style>
