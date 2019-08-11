<template>
  <div>
    <input type="text" v-model="newTodoItem" @keyup.enter="addTodo">
    <button type="button" @click="addTodo">추가</button>
    <modal v-if="showModal" @close="showModal = false">
      <h3 slot="header">경고</h3>
      <button type="button" slot="footer" @click="showModal = false">
        할일을 입력하세요
      </button>
    </modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue';

export default {
  data() {
    return {
      newTodoItem: '',
      showModal: false
    }
  },
  methods: {
    addTodo() {
      if (this.newTodoItem !== '') {
        let value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit('addTodo', value);
        this.clearInput();
      } else {
        this.showModal = !this.showModal;
      }
    },
    clearInput() {
      this.newTodoItem = '';
    }
  },
  components: {
    'Modal': Modal
  }
}
</script>

<style scoped>
</style>