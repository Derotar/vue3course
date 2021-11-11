<template>
  <div v-if="show" class="dialog" @click="HideDialog">
    <div @click.stop class="dialog__content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
  export default {
    props:{
      show : { 
        type: Boolean,
        default: false
      }
    },
    methods : {
      HideDialog(){
        this.$emit('update:show', false)
      }
    }
  }
</script>

<style scoped>
.dialog {
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: #151515;
  opacity: 0.3;
  position: fixed;
  display: flex;
}
.dialog__content {
  margin: auto;
  background: white;
  border-radius: 15px;
  min-height: 50px;
  min-width: 50px;
  padding: 20px;
}
</style>