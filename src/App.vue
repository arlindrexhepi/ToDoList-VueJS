<template>
  <div id="app">
    <b-container>
      <b-form-row>
        <h1 @click="inputState=!inputState" :style="{cursor: cursor}">{{appName}}</h1>
        <b-form-input class="mx-auto w-50, inputField" placeholder="Add New Tasks" v-if="inputState" @keyup.enter="addTask()" v-model="item" /> 
        <b-button class="my-3" variant="outline-primary" @click="addTask()">Add Task</b-button> 
        <ul>
          <li v-for="(task, index) in items" :key="index" :class="{finished: task.finished}" class="my-3" @click="task.finished=!task.finished"><h3> {{task.name}}  <b-button variant="outline-danger" @click.stop="removeTask(index)"> X </b-button></h3></li>
        </ul>
        <b-button v-if="items.length>0" class="my-3" variant="outline-primary" @click="clearAll()">Clear All</b-button> 
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
      appName: 'To Do List Vue.js!',
      item: null,
      items: [],
      inputState: false,
      condition: true,
      editIndex: null,
      cursor: 'pointer'
    }
  },
  computed:{
    
  },
  methods: {
    addTask() {
      if(this.inputState === false){
        this.inputState =!this.inputState
      } else {
        if(this.item.name === null) {
        return;
      } else {
        this.items.unshift({name: this.item, finished:false})
        this.item=null
      }
      return
      }
    },
    removeTask(index) {
      this.items.splice(index, 1)
    },
    clearAll() {
      this.items = []
    }
  }
}
</script>

<style>
html {
  background: linear-gradient(90deg,#1d3557 5%, #457b9d 35%, #a8dadc 95%, #e63946 100%);
}
#app {
  background: linear-gradient(90deg, #fefae0 0%, #f1faee 35%, #f1faee 90%, #fefae0 100%);
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #1d3557;
  margin-top: 60px;
}
li {
  color: #1d3557;
  list-style-type: none;
  cursor: pointer;
  font-weight: bolder;
}
.finished {
  text-decoration: line-through;
  color: gray;
}
h1 {
  font-weight: bolder;
  color: #1d3557;
}
.inputField {
  box-shadow: 5px 5px 5px #1d3557;
}
</style>
