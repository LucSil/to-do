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
  data() {
    return {};
  },
  methods: {},
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
  color: #c1deae;
}
.cont {
  background: #219f94;
  max-width: 400px;
  min-height: 400px;
  margin: 10px auto;
  padding: 10px 0;
  border-radius: 20px;
}
body {
  margin: 0;
  background: #eee;
}
</style>
