<template>
  <footer>
    <p>{{coppyright}} {{title}}</p>
  </footer>
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
      coppyright: "Copyright 2017"
    };
  },
  methods: {},
  created() {
    //สร้างเมื่อเรียก component
    bus.$on("changeTitle", data => {
      this.title = data;
    });
  }
};
</script>

<style scoped>
footer {
  background: #222;
  padding: 6px;
  width: 100%;
  left: 0;
  bottom: 0;
}

p {
  color: lightgreen;
  text-align: center;
}
</style>
