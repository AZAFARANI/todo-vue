<template>
  <loader v-if="loading" />
  <parent v-if="!loading" />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import loader from "./components/loader.vue";

import parent from "./components/showTasks.vue";
@Options({
  components: {
    parent,
    loader,
  },
})
export default class App extends Vue {
  loading = true;

  mounted() {
    setTimeout(() => {
      this.loading = !this.loading;
    }, 1500);
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
