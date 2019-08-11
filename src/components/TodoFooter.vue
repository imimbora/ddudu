<template>
  <div>
    <button type="button" @click="clearTodo">모두 삭제</button>
  </div>
</template>

<script>
  export default {
    methods: {
      clearTodo() {
        // localStorage.clear();
        this.$emit('removeAll');
      }
    }
  }
</script>

<style scoped>

</style>