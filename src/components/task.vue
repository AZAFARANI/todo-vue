<template>
  <div class="taskContainer">
    <h2>{{ task.title }}</h2>

    <div class="btncontainer">
      <h4 v-if="task.done">done!</h4>
      <button id="donebtn" @click="emit" v-if="!task.done">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="20"
          height="20"
          fill="currentColor"
          class="bi bi-check-lg"
          viewBox="0 0 16 16"
        >
          <path
            d="M12.736 3.97a.733.733 0 0 1 1.047 0c.286.289.29.756.01 1.05L7.88 12.01a.733.733 0 0 1-1.065.02L3.217 8.384a.757.757 0 0 1 0-1.06.733.733 0 0 1 1.047 0l3.052 3.093 5.4-6.425a.247.247 0 0 1 .02-.022Z"
          />
        </svg>
      </button>

      <button id="deletebtn" @click="deleteTask">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="20"
          height="20"
          fill="currentColor"
          class="bi bi-trash3-fill"
          viewBox="0 0 16 16"
        >
          <path
            d="M11 1.5v1h3.5a.5.5 0 0 1 0 1h-.538l-.853 10.66A2 2 0 0 1 11.115 16h-6.23a2 2 0 0 1-1.994-1.84L2.038 3.5H1.5a.5.5 0 0 1 0-1H5v-1A1.5 1.5 0 0 1 6.5 0h3A1.5 1.5 0 0 1 11 1.5Zm-5 0v1h4v-1a.5.5 0 0 0-.5-.5h-3a.5.5 0 0 0-.5.5ZM4.5 5.029l.5 8.5a.5.5 0 1 0 .998-.06l-.5-8.5a.5.5 0 1 0-.998.06Zm6.53-.528a.5.5 0 0 0-.528.47l-.5 8.5a.5.5 0 0 0 .998.058l.5-8.5a.5.5 0 0 0-.47-.528ZM8 4.5a.5.5 0 0 0-.5.5v8.5a.5.5 0 0 0 1 0V5a.5.5 0 0 0-.5-.5Z"
          />
        </svg>
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { Task } from "@/models/class";
import { Vue, Options } from "vue-class-component";
import { Prop } from "vue-property-decorator";

export default class propTask extends Vue {
  @Prop() task!: Task;

  emit() {
    this.$emit("handleButtonClick");
  }
  deleteTask() {
    this.$emit("deleteTask");
  }
}
</script>

<style lang="scss">
.taskContainer {
  width: 30%;
  margin: 0 auto;
  padding-bottom: 10px;
  padding: 16px;
  margin-bottom: 15px;
  border-radius: 8px;
  border: none;
  box-shadow: rgba(0, 0, 0, 0.2) 0 3px 5px -1px,
    rgba(0, 0, 0, 0.14) 0 6px 10px 0, rgba(0, 0, 0, 0.12) 0 1px 18px 0;
  display: flex;
  justify-content: space-between;
  background: #fafafa;
}

.btncontainer {
  display: flex;
  gap: 10px;
  justify-content: center;
  align-items: center;
}

#donebtn {
  border-radius: 5px;
  box-shadow: rgba(0, 0, 0, 0.2) 0 3px 5px -1px,
    rgba(0, 0, 0, 0.14) 0 6px 10px 0, rgba(0, 0, 0, 0.12) 0 1px 18px 0;
  border: none;

  padding: 3px 5px;

  background-color: rgb(236, 236, 236);
}

#deletebtn {
  border-radius: 5px;
  box-shadow: rgba(0, 0, 0, 0.2) 0 3px 5px -1px,
    rgba(0, 0, 0, 0.14) 0 6px 10px 0, rgba(0, 0, 0, 0.12) 0 1px 18px 0;
  border: none;

  padding: 3px 5px;
  background-color: rgb(236, 236, 236);
}

button:hover {
  cursor: pointer;
}
</style>
