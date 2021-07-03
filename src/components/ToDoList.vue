<template>
<ul>
  <li v-bind:title="todo">
    {{ todo.slice(0, 10) + '...' }}</li>
</ul>
</template>
<script>
export default {
  data() {
    return { todo: '海に行って、砂遊びを友達とする' }
  }
};
</script>
