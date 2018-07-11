<template>
  <div class="container">
    <h3>{{ title }}</h3>
    <form>
    <textarea placeholder="Add new Task" v-model="newTask"></textarea>
    <p>{{ newTask }}</p>
    <button type="button" v-on:click="addTask">Add Task {{tasks.length}}</button>
    </form>
    <ul>
    <li v-for="task in tasks">{{ task }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      title: 'My Todo List',
      newTask:'This is a sample',
      tasks:[

      ]
    }
  },
  methods:{
  	addTask(){
  		
  		this.tasks.unshift(this.newTask)
  		this.newTask = '';

  	}
  }
}
</script>
