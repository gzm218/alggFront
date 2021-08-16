<template>
  <div class="todo-footer" v-show="total">
    <label>
      <input type="checkbox" v-model="isAll" />
    </label>
    <span>
      <span>已完成{{ donesTotal }}</span> / {{ total }}
    </span>
    <button class="btn btn-danger" @click="clearAll">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: 'Footer',
  props: ['todos'],
  methods: {
    clearAll() {
      this.$emit('clearAllTodo')
    },
  },
  computed: {
    total() {
      return this.todos.length
    },
    donesTotal() {
      //pre 上一次调用函数的返回值
      return this.todos.reduce((pre, todos) => pre + (todos.done ? 1 : 0), 0)
    },
    isAll: {
      get() {
        return this.donesTotal === this.total && this.todos.length != 0
      },
      set(value) {
        this.$emit('checkAllTodo', value)
      },
    },
  },
}
</script>

<style>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>
