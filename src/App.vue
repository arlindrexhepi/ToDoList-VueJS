<template>
  <div id="app">
    <div>
      <h1>To Do List Vue.js</h1>
      <input @keyup.enter="addTask()" v-model="item">
      <button @click="addTask()">Add Task</button>
      <ul>
        <li v-for="(task, index) in items" :key="index" :class="{finished: task.finished}" @click="task.finished=!task.finished"><h3> {{task.name}} <button @click="editTask(index)">Edit</button> <button @click="removeTask(index)"> X </button></h3></li>
      </ul>
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
      editIndex: null,
      cursor: 'pointer'
    }
  },
  computed:{
    
  },
  methods: {
    addTask() {
      if(this.item.name === null) {
        return;
      } else {
        this.items.unshift({name: this.item, finished:false})
        this.item=null
      }
    },
    removeTask(index) {
      this.items.splice(index, 1)
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
  cursor: pointer;
  font-weight: bolder;
}
.finished {
  text-decoration: line-through;
}
</style>
