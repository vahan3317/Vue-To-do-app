<template>
 
 <main>
    <h1>Task Board</h1>
    <p>Create a list of tasks</p>
    <div v-show="$store.state.tasks.length === 10" class="error">
     You can add only 10 tasks!
   </div>
  
   <div class="container">
    <div class="create-new">
      
      <input 
        type="text" 
        v-model="newTask" 
        placeholder="Add a new task" 
        @keypress.enter="addTask" />
      <button @click="addTask">+</button>
    </div>

    <div class="tasks">
      <Task
        v-for="(task, i) in $store.state.tasks"
        :key="i"
        :task="task" />
    </div>
  </div>

  </main>
 
 
</template>

<script>
export default {
 data(){
  return{
    newTask:'',
    error:false
  }
 },
 methods:{
  addTask (){
    if(this.newTask){
      if(this.$store.state.tasks.length <= 10){
      this.$store.commit('ADD_TASK',this.newTask);
      this.newTask ="";
     
        
      }
    }
   
  }
 }
}
</script>
