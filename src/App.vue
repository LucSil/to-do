<template>
  <div class="cont">
    <h1>To-dos</h1>
    <Todo />
  </div>
</template>

<script>
import Todo from "./components/Todo.vue";

export default {
  name: "App",
  components: { Todo },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
#app h1 {
  color: #ecb365;
}
.cont {
  max-width: 600px;
  min-height: 400px;
  margin: 10px auto;
  padding: 10px;
  box-sizing: border-box;
}
body {
  margin: 0;
  background: #041c32;
  cursor: default;
}
</style>
