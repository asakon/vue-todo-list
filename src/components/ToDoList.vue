<template>
<input v-model="inputValue">
<input v-model="filterValue" placeholder="フィルタテキスト">
<button v-on:click="handleClick">
  ToDoを追加
</button>
<ul>
  <li v-for="todo in filterdTodoItems"
    v-bind:key="todo.id"
    v-on:click="todo.done = !todo.done">
    <span v-if="todo.done">✓</span>
    {{ todo.text }}
  </li>
</ul>
</template>
<script>
export default {
  data() {
    return {
      inputValue: '',
      todoItems: [
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
      ],
      filterValue: ''
    }
  },
  computed: {
    filterdTodoItems() {
      if(!this.filterValue) {
        return this.todoItems
      }
      return this.todoItems.filter((todo) => {
        return todo.text.includes(this.filterValue)
      })
    }
  },
  methods: {
    handleClick() {
      this.todoItems.push({
        id: this.todoItems.length + 1,
        text: this.inputValue
      })
      this.inputValue = ''
    }
  }
};
</script>
