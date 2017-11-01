<template>
<div id="app">
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
