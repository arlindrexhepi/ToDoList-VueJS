<template>
  <div id="app">
    <b-container my="3">
      <b-form-row>
        <h1>To Do List Vue.js</h1>
        <b-form-input @keyup.enter="addTask()" v-model="item" />
        <b-button variant="outline-primary" @click="addTask()">Add Task</b-button> 
        <ul>
          <li v-for="(task, index) in items" :key="index" :class="{finished: task.finished}" @click="task.finished=!task.finished"><h3> {{task.name}}  <b-button variant="outline-danger" @click="removeTask(index)"> X </b-button></h3></li>
        </ul>
      </b-form-row>
    </b-container>
  </div>
</template>

<script>
import Vue from 'vue'
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'

import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

Vue.use(BootstrapVue)
Vue.use(IconsPlugin)
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
