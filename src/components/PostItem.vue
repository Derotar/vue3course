<template>
<<<<<<< HEAD
  <!-- eslint-disable -->

=======
>>>>>>> second
  <div class="post">
    <div>
      <div>
        Title: <strong> {{ post.title }} </strong>
      </div>
      <div>
        Description: <strong> {{ post.body }} </strong>
      </div>
    </div>
<<<<<<< HEAD
    <div class="post__btns">
      <MyButton
      @click="$emit('remove', post)">Delete</MyButton>
    </div>
=======
    <MyButton @click="removePost"> Remove </MyButton>
>>>>>>> second
  </div>
</template>

<script>
<<<<<<< HEAD
import MyButton from "../components/UI/MyButton.vue"
export default {
    components : {
        MyButton,
    },
=======
import MyButton from './UI/MyButton.vue';
export default {
  components: { MyButton },
  data() {
    return {};
  },
>>>>>>> second
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
<<<<<<< HEAD
=======
  methods : {
    removePost() {
      this.$emit('remove', this.post);
      console.log("remove in item");
    }
  }
>>>>>>> second
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
<<<<<<< HEAD

</style>
=======
</style>
>>>>>>> second
