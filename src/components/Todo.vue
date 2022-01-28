<template>
  <input
    type="text"
    name="todo"
    id="todo"
    @keyup="send"
    v-model="todoName"
    required
  />
  <ul>
    <li v-for="todo in todos" @click="deleteTodo(todo)" :key="todo.id">
      {{ todo }}
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      todos: ["Go to the theatre", "Get some beef"],
      todoName: "",
    };
  },
  methods: {
    send: function (e) {
      if (this.todoName && e.key === "Enter") {
        if (!this.todos.includes(this.todoName)) {
          this.todos.push(this.todoName);
        }
        this.todoName = "";
      }
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter((item) => {
        return item !== todo;
      });
    },
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
  display: grid;
  justify-items: start;
  width: 80%;
  margin: 10px auto;
}

li {
  color: #aefeff;
  font-size: 15px;
  cursor: pointer;
  margin-bottom: 8px;
}
</style>
