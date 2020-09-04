<template>
  <div class="stats">
      <div v-for="(task, index) in tasks" :key="index">
        <h3>{{ task.title }}</h3>
        <p>{{ task.description }}</p>
        <button @click="delete_task(index)" class="done_btn">Delete</button>
      </div>
      <div class="add_task">
        <input type="text" v-model="newtasks.title" placeholder="New Task">
        <textarea name="add_desk" id="" cols="30" rows="10" v-model="newtasks.description" placeholder="Description"></textarea>
        <button @click="add_task()" class="add_task_btn">➕</button>
      </div>
  </div>
</template>

<script>
export default {
  name: 'Tasks',
  data() {
    return {
      newtasks: {
        title: "",
        description: "",
        status: false
      },
      tasks: [{
        title: "Learn Vue",
        description: "Read a book about Vue 2.0",
        status: true
      }
      ]
    }
  },
  methods: {
    delete_task(index){
      this.tasks.splice(index, 1)
    },
    add_task(){
      if(this.newtasks.title!=''){
        this.tasks.push({
          title: this.newtasks.title,
          description: this.newtasks.description,
        })
        this.newtasks.title ='',
        this.newtasks.description = ''
      }
    },
}
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>


// TODO create feature change status button + change h3 ----
