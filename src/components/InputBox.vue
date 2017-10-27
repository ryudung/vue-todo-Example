<template>
<div>
  <p>
    InputBox
  </p>
  <input type="text" v-model='newItem' v-on:keyup.enter='addItem' />
  <button v-on:click="addItem">아이템 추가</button>
  <button @click="clearLocalStroe">전체 삭제</button>
</div>
</template>
<script>
export default {
  props: ['passedData'],
  data() {
    return {
      newItem: ''
    }
  },
  methods: {
    addItem() {
      let item = this.newItem.trim();
      if (item === '') {
        alert('빈칸은 안됩니다.');
      }
      var value = item;
      localStorage.setItem(value, value);
      this.passedData.push(value);
      this.newItem = '';
    },
    clearLocalStroe() {
      this.$emit('clearLocalStorage');
    }
  }
}
</script>
<style></style>
