<template>
  <div>
    <ul v-if='passedData'>
      <li v-for='(item,index) in passedData'>
            <div>
              <span>{{item}}</span>
              <span><button @click='removeItem(item,index)'>삭제</button></span>
            </div>
      </li>
    </ul>
  </div>
  </template>
<script>
export default {
  props: ['passedData'],
  methods: {
      removeItem(item,index){
            this.$emit('removeTodo', item, index);
      }
  }
}
</script>
<style>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
</style>
