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
  <div class="item" v-for="(todo, index) in todos" :key="index">
    <p>
      {{ todo.item }}
    </p>
    <div class="buttons">
      <button @click="deleteTodo(index)" class="red">❌</button>
      <button class="green">✔</button>
    </div>
  </div>
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
          id: this.todos.length,
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
</style>
