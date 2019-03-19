<template>
  <div id="app">
    <app-header v-bind:title="title" v-on:changeTitle="updateTitle($event)"></app-header>
    <!-- โยนค่าข้ามคอมโพเน้น -->
    <ninjas v-bind:ninjas="ninjas"></ninjas>
    <!--<form-helper>
      <div slot="form-header">
        <h3>This is the title of the form</h3>
        <p>Information about the form</p>
      </div>
      <div slot="form-feilds">
        <input type="text" placeholder="name" required>
        <input type="password" placeholder="password" required>
      </div>
      <div slot="form-controls">
        <button v-on:click="handleSubmit">Submit</button>
      </div>
    </form-helper>-->
    <div id="dynamic">
      <keep-alive>
        <component v-bind:is="component" v-show="condition"></component>
      </keep-alive>
      <button v-on:click="component = 'form-one', condition = true">Show form one</button>
      <button v-on:click="component = 'form-two', condition = true">Show form two</button>
      <button v-on:click="component = 'add-blog', condition = true">Show add blog</button>
    </div>
    <div></div>
    <app-footer v-bind:title="title"></app-footer>
    <!-- เปลี่ยนคอมโพเน้นแบบยืดหยุ่น -->
  </div>
</template>

<script>
import Header from "./components/Header";
import Footer from "./components/Footer";
import Formhelper from "./components/Formhelper";
import formOne from "./components/formOne";
import formTwo from "./components/formTwo";
import addBlog from "./components/addBlog";

export default {
  name: app,
  components: {
    "app-header": Header,
    "app-footer": Footer,
    "form-helper": Formhelper,
    "form-one": formOne,
    "form-two": formTwo,
    "add-blog": addBlog
  },
  name: "app",
  data() {
    return {
      loading: true,
      ninjas: [
        { name: "Ryu", speciality: "Vue Components", show: false },
        { name: "Crystal", speciality: "HTML wizzard", show: false },
        { name: "Hitoshi", speciality: "Click Event", show: false },
        { name: "Tango", speciality: "Conditionals", show: false },
        { name: "Kami", speciality: "Webpack", show: false },
        { name: "Yoshi", speciality: "Data Diggin", show: false }
      ],
      title: "Vue Ninjas",
      component: "form-one",
      condition: false
    };
  },
  methods: {
    updateTitle(updatedTitle) {
      this.title = updatedTitle;
    }
  }
};
</script>

<style>
#dynamic {
  text-align: center;
  padding-bottom: 10px;
}
</style>
