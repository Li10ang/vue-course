<template>
  <div id="app">
    <div>
      <input type="text" v-model="info">
      <button @click="handleClick">添加</button>
    </div>
    <ul>
      <todo-item v-for="item in list" :key="item" >
        <template v-slot:item="itemProps">
          {{itemProps}}
          <span :style="{fontSize: '20px', color: itemProps.checked ? 'red' : 'blue'}">{{item}}</span>
        </template>
      </todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem.vue";

export default {
  name: "app",
  components: {
    TodoItem
  },
  data() {
      return {
          info: '',
          list: [],
      }
  },
  methods: {
      handleClick(){
          this.list.push(this.info);
          this.info = '';
      }
  },
}
</script>

<style>

</style>
