<template>
<input v-model="inputValue">
<button v-on:click="handleClick">
  入力内容を表示
</button>
<ul>
  <li v-for="todo in todoItems"
    v-bind:key="todo.id">
    {{ todo.text }}</li>
</ul>
</template>
<script>
export default {
  data() {
    return {
      inputValue: '',
      todoItems: [
        { id: 1, text: '海に行って、砂遊びを友達とする' },
        { id: 2, text: '図書館に行って、マンガを借りる' }
      ]
    } 
  },
  methods: {
    handleClick() {
      alert(this.inputValue)
    }
  }
};
</script>
