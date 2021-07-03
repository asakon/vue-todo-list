<template>
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
      todoItems: [
        { id: 1, text: '海に行って、砂遊びを友達とする' },
        { id: 2, text: '図書館に行って、マンガを借りる' }
      ]
    } 
  }
};
</script>
