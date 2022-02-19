<template>
  <input
    type="text"
    name="todo"
    id="todo"
    @keyup="send"
    v-model="todoName"
    placeholder="Input to-do"
    required
  />
  <div class="item" v-for="todo in todos" :key="todo">
    <p>
      {{ todo }}
    </p>
    <div class="buttons">
      <button @click="deleteTodo(todo)" class="red">❌</button>
      <button @click="completeTodo(todo)" class="green">✔</button>
    </div>
  </div>

  <div class="completed"></div>
</template>

<script>
export default {
  name: "Todo",
  emits: ["complete"],

  data() {
    return {
      completedTodos: [],
      todos: ["Spy on the kids", "Practice Romanian"],
      todoName: "",
    };
  },
  methods: {
    send: function (e) {
      if (this.todoName && e.key === "Enter") {
        this.todos.push(this.todoName);
        this.todoName = "";
        console.log(this.todos);
      }
    },

    deleteTodo(todo) {
      this.todos = this.todos.filter((item) => item !== todo);
    },
    completeTodo(todo) {
      this.completedTodos.push(this.todos.splice(todo, 1));
      console.log(this.completedTodos);
      this.$emit("complete", this.completedTodos);
    },
  },
};
</script>

<style>
input {
  width: 60%;
  border: none;
  background: none;
  border-bottom: 2px solid #51c4d3;
  color: #132c33;
  font-size: 1.2em;
  border-radius: 2px;
  padding: 10px 0 10px 10px;
  margin-bottom: 30px;
  outline: none;
}
.item {
  max-width: 60%;
  margin: 0 auto 15px auto;
  padding: 5px;
  display: grid;
  grid-template-columns: 70% 30%;
  border: 2px solid transparent;
  border-radius: 5px;
  box-shadow: 2px 3px 5px 1px #51c4d3;
}
.item p {
  color: #132c33;
  font-weight: 600;
  padding: 10px 5px;
  margin: 0;
  text-align: left;
}

.buttons {
  display: flex;
  margin: 0;
  padding: 0;
  justify-content: space-evenly;
  align-items: center;
}

button {
  cursor: pointer;
  background: none;
  border: none;
  font-weight: bold;
  font-size: 13px;
}

.green {
  color: green;
  font-size: 15px;
}

/* completed component */
.completed h1 {
  margin-top: 2em;
  color: #51c4d3;
}
</style>
