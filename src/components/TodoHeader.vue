<template>
  <!-- 输入框 -->
  <header class="header">
    <h1>TODOメモ帳</h1>
    <input placeholder="TODOを入力してください" class="new-todo" v-model.trim="inputMsg" @keyup.enter="add" />
    <button class="add" @click="add">TODO追加</button>
  </header>
</template>

<script>
export default {
  data() {
    return {
      inputMsg: ''
    }
  },
  methods: {
    add() {
      this.$emit('add', this.inputMsg)
      this.inputMsg = ''
    }
  }
}

</script>

<style></style>