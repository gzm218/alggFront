<template>
  <div>
    <li>
      <label>
        <input
          type="checkbox"
          :checked="todos.done"
          @change="handleCheck(todos.id)"
        />
        <span>{{ todos.title }}</span>
      </label>
      <button class="btn btn-danger" @click="deleteTodos(todos.id)">
        删除
      </button>
    </li>
  </div>
</template>

<script>
export default {
  name: 'Todos',
  props: ['todos', 'delTodos', 'checkTodos'],
  methods: {
    deleteTodos(id) {
      if (confirm('确定删除吗？')) {
        this.delTodos(id)
      }
    },
    handleCheck(id) {
      this.checkTodos(id)
    },
  },
}
</script>

<style scoped>
/*todo*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
li:hover {
  background-color: #ddd;
}

li:hover button {
  display: block;
}
</style>
