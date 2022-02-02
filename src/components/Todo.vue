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
  <ul>
    <li class="outer_li" v-for="(todo, index) in todos" :key="index">
      {{ todo.item }}
      <div class="buttons">
        <button @click="deleteTodo(index)" class="red">❌</button>
        <button class="green">✔</button>
      </div>
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
  width: 90%;
  border: none;
  background: none;
  border-bottom: 2px solid #064663;
  color: #fff2f9;
  font-size: 1.2em;
  border-radius: 2px;
  padding: 10px 0 10px 10px;
  margin-bottom: 10px;
  outline: none;
}

ul {
  width: 85%;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #ecb365;
  margin-bottom: 15px;
  font-size: 15pt;
}
.buttons {
  margin: 0;
}

button {
  cursor: pointer;
  background: none;
  border: none;
  font-weight: bold;
  font-size: 13px;
}
.red {
  margin-right: 5px;
}
.green {
  color: green;
}
</style>
