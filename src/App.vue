<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div>
      <h1>To Do List Vue.js</h1>
      <ul>
        <li v-for="(task, index) in items" :key="index"><h3 :style="{ textDecoration: finished}"> {{task}}  <button @click="finishedTask()">Finished</button> <button @click="removeTask()"> X </button></h3></li>
      </ul>
      <input @keyup.enter="addTask()" v-model="item">
      <button @click="addTask()">Add Task</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      item: null,
      items: [],
      condition: true,
      finished: null
    }
  },
  computed:{
    
  },
  methods: {
    addTask() {
      if(this.item === null) {
        return;
      } else {
        this.items.push(this.item)
        this.item = null
      }
    },
    removeTask(e) {
      this.items.splice(e, 1)
    },
    finishedTask() {
      if(this.condition == false ? this.finished='none': this.finished='line-through') {
        this.condition=!this.condition
        }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
li {
  list-style-type: none;
}
</style>
