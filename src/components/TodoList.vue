<template>
  <div class="todo-list">
    <h1>Hero List</h1>
    <input
      type="text"
      v-model="newTodo"
      @keyup.enter="addTodo"
      placeholder="Type Hero name here"
    />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <span :class="{ done: todo.done }">
          {{ todo.text }}
        </span>
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== "") {
        this.todos.push({ text: this.newTodo, done: false });
        this.newTodo = "";
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.todo-list {
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
}

input {
  width: calc(100% - 22px);
  padding: 10px;
  margin-bottom: 20px;
  font-size: 16px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background: #f4f4f4;
  margin-bottom: 10px;
  border-radius: 4px;
}

li span {
  cursor: pointer;
}

li span.done {
  text-decoration: line-through;
  color: #888;
}

button {
  background: #ff6b6b;
  border: none;
  color: white;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 4px;
}

button:hover {
  background: #ff4949;
}
</style>
