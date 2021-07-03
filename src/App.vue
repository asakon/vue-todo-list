<template>
<ul>
  <li>{{ todo }}</li>
</ul>
</template>


<script>
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'App',
  components: {
    ToDoList
  },
  data() {
    return { todo: '海に行く' }
  }
}
</script>
