<template>
<input v-model="inputValue">
<input v-model="filterValue" placeholder="フィルタテキスト">
<button v-on:click="handleClick">
  ToDoを追加
</button>
<ul>
  <ToDoItem v-for="todo in filterdTodoItems"
    v-bind:key="todo.id"
    v-bind:text="todo.text"
    v-bind:done="todo.done"
  />
</ul>
</template>
<script>
import ToDoItem from './ToDoItem.vue'
export default {
  components: { ToDoItem },
  data() {
    const todoItems = [
      {
        id: 1,
        done: false,
        text: '海に行って、砂遊びを友達とする'
      },
      {
        id: 2,
        done: false,
        text: '図書館に行って、マンガを借りる'
      }
    ]
    return {
      inputValue: '',
      todoItems,
      filterdTodoItems: todoItems,
      filterValue: ''
    }
  },
  watch: {
    filterValue() {
      this.updateFilteredToDoItems()
    },
    todoItems: {
      handler() {
        this.updateFilteredToDoItems()
      },
      deep: true
    },
  },
  methods: {
    handleClick() {
      this.todoItems.push({
        id: this.todoItems.length + 1,
        text: this.inputValue
      })
      this.inputValue = ''
    },
    updateFilteredToDoItems() {
      this.filterdTodoItems = 
        this.filterValue 
          ? this.todoItems.filter((todo) =>
            todo.text.includes(this.filterValue)
          )
          : this.todoItems
    }
  }
}
</script>
<style>
.todo-item.done {
  background-color: #3fb983;
  color: #fff;
}
</style>