<template>
  <h1>welcome to your TODO-list</h1>
  <propTask
    v-for="(t, i) in Tasks"
    :key="i"
    :task="t"
    @handleButtonClick="
      () => {
        handleclick(i);
      }
    "
    @deleteTask="() => handleDeleteTask(i)"
  />

  <addTask @handleAddTask="showNewTask($event)" />
</template>

<script lang="ts">
import { Task } from "@/models/class";
import { Options, Vue } from "vue-class-component";
import propTask from "./task.vue";
import addTask from "./addTasks.vue";

@Options({
  components: {
    propTask,
    Task,
    addTask,
  },
})
export default class parent extends Vue {
  Tasks: Task[] = [new Task("Study"), new Task("exercise"), new Task("clean")];

  handleclick(i: number) {
    this.Tasks[i].done = true;
  }

  showNewTask(newTask: string) {
    let newTodo = new Task(newTask);
    this.Tasks.push(newTodo);
  }

  handleDeleteTask(i: number) {
    this.Tasks.splice(i, 1);
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
