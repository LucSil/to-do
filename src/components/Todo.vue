<template>
  <input
    type="text"
    name="todo"
    id="todo"
    @keyup.enter="send"
    v-model="todoName"
    placeholder="Input to-do"
    required
  />
  <div v-for="(todo, index) in todos" :key="index">
    <div :class="[todo.done ? 'itemComplete' : 'item']">
      <p>
        {{ todo.item }}
      </p>
      <div class="buttons">
        <button @click="deleteTodo(index)" class="red">&times;</button>
        <button @click="completeTodo(index)" class="green">&check;</button>
      </div>
    </div>
  </div>
</template>

<script>
import { reactive, ref } from "@vue/reactivity";

export default {
  name: "Todo",
  setup() {
    const todos = reactive([
      {
        item: "Learn Vue.js",
        id: 1,
        done: false,
      },
      {
        item: "Create an app",
        id: 2,
        done: false,
      },
    ]);

    const todoName = ref("");

    const send = () => {
      if (todoName.value) {
        todos.unshift({
          item: todoName.value,
          id: todos.length,
          done: false,
        });
        todoName.value = "";
      }
    };

    const deleteTodo = (index) => {
      todos.splice(index, 1);
    };

    const completeTodo = (index) => {
      todos[index].done = true;
    };

    return { todos, todoName, send, deleteTodo, completeTodo };
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
.itemComplete {
  max-width: 60%;
  margin: 0 auto 15px auto;
  padding: 5px;
  display: grid;
  grid-template-columns: 70% 30%;
  border: 2px solid transparent;
  background: #d8e3e7;
  border-radius: 5px;
  box-shadow: 2px 3px 5px 1px #4e9f3d;
}
.itemComplete p {
  color: green;
  font-weight: 600;
  padding: 10px 5px;
  margin: 0;
  text-align: left;
}
.item p {
  color: crimson;
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

.red {
  color: red;
  font-size: 15px;
}
.green {
  color: green;
  font-size: 15px;
}
</style>
