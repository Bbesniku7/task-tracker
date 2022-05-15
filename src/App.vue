<template>
  <div class="container">
    <Header
      @btn-click="showForm()"
      title="Task Tracker"
      :showAddTask="showAddTask"
    />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks
      :tasks="tasks"
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
    />
  </div>
</template>


<script>
// Import Components
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    showForm() {
      this.showAddTask = !this.showAddTask;
    },
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    deleteTask(id) {
      if (confirm("Are you sure you want to Delete?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      if (confirm("You want to toggle ON / OFF reminder ?")) {
        this.tasks = this.tasks.map((task) =>
          task.id === id ? { ...task, reminder: !task.reminder } : task
        );
      }
    },
  },
  created() {
    this.tasks = [
      {
        id: "1",
        text: "Ujiti Lulet t hanen",
        reminder: true,
        day: "May  1st at 4:30pm",
      },
      {
        id: "2",
        text: "Takim",
        reminder: true,
        day: "May  2st at 6:30pm",
      },
      {
        id: "3",
        text: "Me msu vue",
        reminder: false,
        day: "May  5st at 9:30pm",
      },
    ];
  },
};
</script>


<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
