<template>
  <input
    type="text"
    name="todo"
    id="todo"
    @keyup="send"
    v-model="todoTrack"
    required
  />
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.item }}
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
          item: "Go to the theatre",
        },
        {
          id: 1,
          item: "Get some beef",
        },
      ],
      todoTrack: "",
    };
  },
  methods: {
    send: function (e) {
      if (this.todoTrack && e.key === "Enter") {
        this.todos.push(this.todoTrack);
      }
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
  margin-bottom: 8px;
}
</style>
