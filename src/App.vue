<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <!-- v-bind directive를 사용하여 data의 todos 객체배열을 props로 내릴 수 있도록 bind한다 -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from "./components/layout/Header";
import AddTodo from "./components/AddTodo";

export default {
  name: "app",
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Nginx공부하기",
          completed: false
        },
        {
          id: 2,
          title: "SVN 공부하기",
          completed: false
        },
        {
          id: 3,
          title: "Vue 정복하기",
          completed: true
        }
      ]
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
