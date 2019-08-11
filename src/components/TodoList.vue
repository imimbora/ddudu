<template>
    <section>
      <transition-group name="list" tag="ul">
        <li v-for="(todoItem, index) in propsdata" :key="todoItem">
          {{ todoItem }}
          <button type="button" @click="removeTodo(todoItem, index)">삭제</button>
        </li>
      </transition-group>
    </section>
</template>

<script>
  export default {
    props: ['propsdata'],
    methods: {
      removeTodo(todoItem, index) {
        this.$emit('removeTodo', todoItem, index);
      }
    }
  }
</script>

<style scoped>
ul {list-style-type:none; text-align:left;}
.list-move {transition:transform 1s;}
.list-enter-active, .list-leave-active {transition:all 1s;}
.list-enter, .list-leave-to {opacity:0; transform:translateY(10px);}
</style>