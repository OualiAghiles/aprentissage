<template>
  <div id="app">
      <div class="container">
        <todo></todo>
      </div>

  </div>
</template>

<script>
import todo from './components/Todolist.vue';

export default {
  name: 'app',
  components: {
    todo,
  },
};
</script>

<style lang="scss">
@import "~bulma/bulma";
body{
  background-color: #e6e9f2;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
