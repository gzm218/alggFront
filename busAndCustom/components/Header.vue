<template>
  <div class="todo-header">
    <input
      v-model="inputValue"
      @keyup.enter="add"
      type="text"
      placeholder="请输入你的任务名称，按回车键确认"
    />
  </div>
</template>

<script>
import { nanoid } from 'nanoid'
export default {
  name: 'Header',
  data() {
    return {
      inputValue: '',
    }
  },
  // props: ['addTodo'],
  methods: {
    add() {
      if (!this.inputValue) return alert('任务名称不为空')
      const addObj = { id: nanoid(), title: this.inputValue, done: false }
      // this.addTodo(addObj)
      this.$emit('addTodo', addObj)
      this.inputValue = ''
    },
  },
}
</script>

<style>
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
    0 0 8px rgba(82, 168, 236, 0.6);
}
</style>
