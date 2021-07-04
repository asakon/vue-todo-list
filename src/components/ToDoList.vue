<template>
<input v-model="inputValue">
<input v-model="filterValue" placeholder="フィルタテキスト">
<button v-on:click="handleClick">
  ToDoを追加
</button>
<ul>
  <li v-for="todo in filterdTodoItems"
    v-bind:key="todo.id"
    class="todo-item"
    v-bind:class="{'done': todo.done}"
    v-on:click="todo.done = !todo.done">
    <span v-if="todo.done">✓</span>
    {{ todo.text }}
  </li>
</ul>
</template>
<script>
export default {
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