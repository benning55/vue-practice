<template>
  <div id="app1">
    <el-row>
      <el-button>Default</el-button>
      <el-button type="primary" @click="loading = !loading">Primary</el-button>
      <el-button type="success">Success</el-button>
      <el-button type="info">Info</el-button>
      <el-button type="warning">Warning</el-button>
      <el-button type="danger">Danger</el-button>
    </el-row>
    <div>
      <el-button type="primary" :loading="loading">Loading</el-button>
      <button type="button" class="btn btn-warning">Warning</button>
    </div>
    <div class="container">
      <form>
        <div class="form-group">
          <label for="exampleInputEmail1">Email address</label>
          <input
            type="email"
            class="form-control"
            id="exampleInputEmail1"
            aria-describedby="emailHelp"
            placeholder="Enter email"
          >
          <small
            id="emailHelp"
            class="form-text text-muted"
          >We'll never share your email with anyone else.</small>
        </div>
        <div class="form-group">
          <label for="exampleInputPassword1">Password</label>
          <input
            type="password"
            class="form-control"
            id="exampleInputPassword1"
            placeholder="Password"
          >
        </div>
        <div class="form-group form-check">
          <input type="checkbox" class="form-check-input" id="exampleCheck1">
          <label class="form-check-label" for="exampleCheck1">Check me out</label>
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
      </form>
    </div>
    <div
      v-bind:class="{done: done}"
      class="container align-middle"
      style="text-align: -webkit-center;"
    >
      <div id="canvas" v-on:mousemove="updateXY">{{x}}, {{y}}</div>
    </div>
    <button
      type="submit"
      class="btn btn-primary"
      style="background-color: red;"
      v-on:click="done = !done"
    >Submit</button>
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <label>Name:</label>
          <input type="text" v-on:keyup.enter="logName" v-model="name">
          <span>{{name}}</span>
        </div>
      </div>
    </div>
    <div>
      <h1>Looping in array</h1>
    </div>
    <ul>
      <li v-for="value in characters" :key="value.id">{{value}}</li>
    </ul>
    <ul>
      <li
        v-for="(ninja, index) in ninjas"
        :key="ninja.id"
      >{{index}}. name: {{ninja.name}} - Age: {{ninja.age}}</li>
    </ul>
    <div>
      <!-- BagImage -->
      <div id="bag" v-bind:class="{ burst: ended }"></div>
      <!-- BagHealth -->
      <div id="bag-health">
        <div v-bind:style="{width: health + '%'}"></div>
      </div>
      <!-- BagControl -->
      <div id="control">
        <button v-on:click="punch" v-show="!ended">Punch</button>
        <button v-on:click="restart">Restart</button>
      </div>
    </div>
    <br>
    <h1>Ninja App</h1>
    <ninja></ninja>
    <div style="padding: 5000px; positon: fixed;"></div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app1",
  components: {
    HelloWorld
  },
  data() {
    return {
      loading: true,
      x: 0,
      y: 0,
      name: "",
      done: false,
      characters: ["mario", "ben", "muse", "naruto"],
      ninjas: [
        { name: "Benning", age: 20 },
        { name: "Muse", age: 21 },
        { name: "lufy", age: 50 }
      ],
      health: 100,
      ended: false
    };
  },
  methods: {
    updateXY: function(event) {
      this.x = event.offsetX;
      this.y = event.offsetY;
    },
    logName: function() {
      alert(this.name);
    },
    notShow: function() {
      if (this.done == true) {
        this.done = false;
      } else {
        this.done = true;
      }
    },
    punch: function() {
      this.health -= 10;
      if (this.health <= 0) {
        this.ended = true;
      }
    },
    restart: function() {
      this.health = 100;
      this.ended = false;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#canvas {
  width: 600px;
  padding: 200px 20px;
  text-align: center;
  border: 1px solid black;
}

.done {
  display: none;
}
#bag {
  width: 200px;
  height: 500px;
  margin: 0 auto;
  background: url(./assets/bag.png) center no-repeat;
  background-size: 80%;
}
#bag-health {
  width: 200px;
  border: 2px solid #000;
  margin: 0 auto 20px auto;
}
#bag-health div {
  height: 20px;
  background: crimson;
}

#control {
  width: 120px;
  margin: 0 auto;
}

#bag.burst {
  background: url(./assets/bag-burst.png) center no-repeat;
  background-size: 80%;
}
</style>
