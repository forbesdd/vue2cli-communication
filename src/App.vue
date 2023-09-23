<template>
  <div id="app">
    <TodoHeader @add="add"></TodoHeader>
    <TodoMain :list="list" @del="del"></TodoMain>
    <TodoFooter :list="list" @allDel="allDel"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoMain from './components/TodoMain.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
  name: 'App',
  components: {
    TodoHeader,
    TodoMain,
    TodoFooter
  },
  data() {
    return {
      list: JSON.parse(localStorage.getItem('list')) || [
        { id: 1, name: '音楽' },
        { id: 2, name: 'スポーツ' },
        { id: 3, name: '映画' }

      ]
    }

  },
  methods: {
    del(newVal) {
      this.list = newVal
    },
    add(inputMsg) {

      if (!inputMsg) {
        alert('TODOを入力してください')
        return
      }

      this.list.unshift({
        id: +new Date(),
        name: inputMsg
      })
    },
    allDel() {
      this.list = []
    }
  },
  watch: {
    list: {
      deep: true,
      handler(newVal) {
        localStorage.setItem('list', JSON.stringify(newVal))
      }
    }
  }

}
</script>

<style></style>
