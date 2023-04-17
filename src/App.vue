<template>
  <div class="container">
    <TaskHeader title="VueGo." />
    <AddTask @add-task="addTask"/>
    <Tasks
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import TaskHeader from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask"

export default {
  name: "App",
  components: {
    TaskHeader,
    Tasks,
    AddTask, 
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm("Are you sure you want to Delete?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
       );
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "March 1st at 2:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Meeting at School",
        day: "March 3rd at 1:30pm",
        reminder: true,
      },
      {
        id: 3,
        text: "Food Shopping",
        day: "March 3rd at 11:00am",
        reminder: false,
      },
    ];
  },
};
</script>

<style></style>
