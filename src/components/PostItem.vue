<template>
  <div class="post">
    <div>
      <div>
        Title: <strong> {{ post.title }} </strong>
      </div>
      <div>
        Description: <strong> {{ post.body }} </strong>
      </div>
    </div>
    <MyButton @click="removePost"> Remove </MyButton>
  </div>
</template>

<script>
import MyButton from './UI/MyButton.vue';
export default {
  components: { MyButton },
  data() {
    return {};
  },
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
  methods : {
    removePost() {
      this.$emit('remove', this.post);
      console.log("remove in item");
    }
  }
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
