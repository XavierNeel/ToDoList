<template>
  <div id="app">
    <Todo></Todo>
  </div>
</template>

<script>
import Todo from "./components/TodoList.vue"

export default {
  name: 'App',
  components:{
    Todo
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto%3Awght%40300%3B400%3B700&display=swap');

#app {
  font-family: 'Roboto', sans-serif;
}

</style>
