<template>
<div id="app">
  <img src="./assets/logo.png">

  <InputBox v-bind:passedData="todoItems" v-on:clearLocalStorage="clearLocalStorage"></InputBox>
  <ItemList v-bind:passedData="todoItems" v-on:removeTodo="removeTodo"></ItemList>

</div>
</template>

<script>
import ItemList from './components/ItemList.vue';
import InputBox from './components/InputBox.vue';


export default {
  name: 'app',
  data() {
    return {
      todoItems: []
    }
  },
  created() {
    for (var key in localStorage) {
      this.todoItems.push(key);
    }
  },
  methods: {
    clearLocalStorage() {
      localStorage.clear();
      this.todoItems = [];
    },
    removeTodo(item, index) {
      this.todoItems.splice(index, 1);
      localStorage.removeItem(item);
    }
  },
  components: {
    ItemList: ItemList,
    InputBox: InputBox
  }
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

h1,
h2 {
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
</style>
