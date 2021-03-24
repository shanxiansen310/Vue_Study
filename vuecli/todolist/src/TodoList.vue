<template>
  <div>
    <div>
      <input v-model="inputValue">
      <button @click="handleSubmit">Submit</button>
    </div>
    <ul>
      <todo-item
        v-for="(item,index) of list"
        :key="index"
        v-bind:content="item"
        v-bind:index="index"
        @delete="handleDelete"
      ></todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem'

export default {
  /* 这两种声明方法都是可以的!!!  */
  components: {
    TodoItem, // template中命名为<TodoItem>
    todoItem: TodoItem, // template中命名为<todo-item>
    'todo-item': TodoItem // template中命名为<todo-item>
  },
  /* 在这里必须要以函数的形式返回 */
  data () {
    return {
      inputValue: '',
      list: []
    }
  },
  methods: {
    handleSubmit () {
      this.list.push(this.inputValue)
      this.inputValue = ''
    },
    handleDelete (index) {
      this.list.splice(index, 1) // index是由子组件传递过来的
    }
  }
}
</script>

<style>

</style>
