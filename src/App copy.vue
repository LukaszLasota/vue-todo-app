<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />
  <h1 v-if="counter == 3">{{ title }}</h1>
  <h2 v-else>{{ counterMultily }}</h2>
  <button @click="increaseCounter">+1</button>
  <br />
  <br />
  <button @click="decreseCounter">-1</button>
  <ul>
    <li v-for="user in users" v-bind:key="user.name">{{ user.name }}</li>
  </ul>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data: function () {
    return {
      title: "My app",
      counter: 0,
      users: [{ name: "Łukasz" }, { name: "Piotrek" }, { name: "Dawid" }],
    };
  },
  computed: {
    counterMultily() {
      return this.counter * 2;
    },
  },
  watch: {
    counter: function () {
      alert(this.counter);
    },
  },
  methods: {
    increaseCounter() {
      this.counter++;
    },
    decreseCounter() {
      this.counter--;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
