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
    <li v-for="(todo, index) in todos" :key="index">
      {{ todo.item }}
      <button @click="deleteTodo(index)">Done</button>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      todos: [
        {
          id: 0,
          item: "Spy on the kids",
        },
        {
          id: 1,
          item: "Practice Romanian",
        },
      ],
      todoName: "",
    };
  },
  methods: {
    send: function (e) {
      if (this.todoName && e.key === "Enter") {
        this.todos.push({
          id: this.todos.length + 1,
          item: this.todoName,
        });
        this.todoName = "";
        console.log(this.todos);
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
input {
  width: 80%;
  border: none;
  background: none;
  border-bottom: 2px solid #9d5353;
  color: #fff2f9;
  font-size: 1.2em;
  border-radius: 2px;
  padding: 10px 0 10px 10px;
  margin-bottom: 10px;
  outline: none;
}

ul {
  width: 80%;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #bf8b67;
  font-size: 15pt;
  margin-bottom: 8px;
}
button {
  cursor: pointer;
  background: #dacc96;
  border: none;
  border-radius: 3px;
  padding: 2px 5px;
  color: #9d5353;
  font-weight: bold;
  font-size: 11px;
  letter-spacing: 1px;
}
</style>
