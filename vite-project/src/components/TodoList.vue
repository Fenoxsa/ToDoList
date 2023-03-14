<script>
  export default {
    data() {
      return {
        newTask: '',
        tasks: []
      }
    },
    methods: {
      addTask() {
        if (this.newTask.trim() !== '') {
          this.tasks.push({
            name: this.newTask,
            done: false
          });
          this.newTask = '';
        }
      },
      deleteTask(index) {
        this.tasks.splice(index, 1);
      },
      deleteDoneTasks() {
        this.tasks = this.tasks.filter(task => !task.done);
      }
    }
  }
</script>

<template>
    <div>
      <h1>TodoList</h1>
      <form @submit.prevent="addTask" style="margin-bottom:20px">
        <input type="text" v-model="newTask">
      </form>
      <ul  v-for="(task, index) in tasks" :key="index">
          <input type="checkbox" v-model="task.done">
          <span :class="{ done: task.done }">{{ task.name }}</span>
          <button @click="deleteTask(index)">X</button>
        
      </ul>
      <button @click="deleteDoneTasks">Supprimer toutes les tâches terminées</button>
    </div>
</template>
  
<style>
.done {
text-decoration: line-through;
}
</style>
  