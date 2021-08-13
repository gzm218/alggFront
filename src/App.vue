<template>
  <div id="app">
    <div class="todo-container">
      <div class="todo-wrap">
        <Header :addTodo="addTodo"></Header>
        <List
          :todos="todos"
          :delTodos="delTodos"
          :checkTodos="checkTodos"
        ></List>
        <Footer
          :todos="todos"
          :checkAllTodo="checkAllTodo"
          :clearAllTodo="clearAllTodo"
        ></Footer>
      </div>
    </div>
  </div>
</template>

<script>
import Footer from './components/Footer.vue'
import Header from './components/Header.vue'
import List from './components/List.vue'
export default {
  name: 'App',
  components: { Footer, Header, List },
  data() {
    return {
      todos: JSON.parse(localStorage.getItem('todos')) || [],
    }
  },
  methods: {
    addTodo(addObj) {
      this.todos.unshift(addObj)
    },
    delTodos(id) {
      //filterg过滤
      this.todos = this.todos.filter((todo) => todo.id !== id)
    },
    checkTodos(id) {
      this.todos.forEach((todos) => {
        if (todos.id === id) todos.done = !todos.done
      })
    },
    checkAllTodo(done) {
      this.todos.forEach((todos) => {
        todos.done = done
      })
    },
    clearAllTodo() {
      this.todos = this.todos.filter((todos) => {
        return !todos.done
      })
    },
  },
  watch: {
    todos: {
      deep: true,
      handler(value) {
        localStorage.setItem('todos', JSON.stringify(value))
      },
    },
  },
}
</script>

<style>
body {
  background: #fff;
}

.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2),
    0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
