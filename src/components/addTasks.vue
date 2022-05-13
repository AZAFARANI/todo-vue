<template>
  <h2>Add new task:</h2>
  <input type="text" v-model="newTask" />
  <button id="submit" @click="addTask">Submit</button>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Prop } from "vue-property-decorator";

export default class addTask extends Vue {
  @Prop() newTask = "";
  addTask() {
    this.$emit("handleAddTask", this.newTask);
  }
}
</script>

<style>
#submit {
  background-color: blue;
  border: none;

  color: white;

  padding: 3px 7px;
  border-radius: 5px;

  margin-left: 5px;

  box-shadow: rgba(0, 0, 0, 0.2) 0 3px 5px -1px,
    rgba(0, 0, 0, 0.14) 0 6px 10px 0, rgba(0, 0, 0, 0.12) 0 1px 18px 0;

  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
