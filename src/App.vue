<template>
  <div id="app">
    <headerTodo></headerTodo>
    <inputTodo v-on:inputData="addTodo"></inputTodo>
    <list v-bind:listData="todoItems"></list>
    <footerTodo></footerTodo>
  </div>
</template>

<script>

import headerTodo from './components/Header.vue'
import inputTodo from './components/Input.vue'
import list from './components/List.vue'
import footerTodo from './components/Footer.vue'

export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      todoItems: []
    }
  },

  created() {
      if(localStorage.length > 0) {
          for(let i = 0; i<localStorage.length; i++) {
              this.todoItems.push(localStorage.key(i));
          }

          // for(let data in localStorage) {
          //  console.log(`data is a ${data}`);
          //  this.todoItems.push(localStorage.key(data));
          // }
      }
  },
  components: {
      headerTodo: headerTodo,
      inputTodo: inputTodo,
      list: list,
      footerTodo: footerTodo
  },
  methods: {
    addTodo(value) {
      localStorage.setItem(value, value); //localStorage는 key,value 쌍으로 저장됨, 경로 -> application/localstorage
      this.todoItems.push(value);
    },
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

body {
  text-align: center;
  background-color: #F6F6F8;
}

input {
  border-style: groove;
  width:200px;
}

button {
  border-style: groove;
}

.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
