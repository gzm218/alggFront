<template>
  <ul class="todo-main">
    <Todos v-for="todoObj in todos" :key="todoObj.id" :todos="todoObj"></Todos>
  </ul>
</template>

<script>
import Todos from './Todos.vue'
export default {
  name: 'List',
  components: { Todos },
  props: ['todos'],
}
</script>

<style>
/*List*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>
