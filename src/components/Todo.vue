<template>
  <input type="text" name="todo" id="todo" />
  <ul v-for="todo in todos" :key="todo.id">
    <li>{{ todo.item }}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      todos: [
        {
          id: 0,
          item: "Go to the theatre",
        },
        {
          id: 1,
          item: "Get some beef",
        },
      ],
    };
  },
};
</script>

<style>
input {
  width: 80%;
  border: none;
  background: none;
  border-bottom: 2px solid #35858b;
  color: #fff2f9;
  font-size: 1.2em;
  border-radius: 2px;
  padding: 10px 0 10px 10px;
  margin-bottom: 10px;
  outline: none;
}

ul {
  width: 80%;
  color: #e8e8a6;
  margin: 10px auto 0 auto;
  display: flex;
  justify-content: start;
  align-items: center;
}
li {
  color: #aefeff;
  font-size: 15px;
  border-radius: 5px;
}
</style>
