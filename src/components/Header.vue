<template>
  <header>
    <h1 v-on:click="changeTitle">{{title}}</h1>
  </header>
</template>

<script>
import { bus } from "../main.js";
export default {
  props: {
    title: {
      type: String
    }
  },
  data() {
    return {
      title: "Vue Ninja"
    };
  },
  methods: {
    changeTitle() {
      //this.$emit("changeTitle", "VueWizzard");
      //this.title = "Vue Wizzard";
      bus.$emit("changeTitle", "VueWizzard");
    }
  }
};
</script>

<style scoped>
header {
  background: lightgreen;
  padding: 10px;
}

h1 {
  color: #222;
  text-align: center;
}
</style>
