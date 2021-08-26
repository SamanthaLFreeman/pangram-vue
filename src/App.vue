<template>
  <main id="app">
    <header class="header">
      <h1>{{ msg }}</h1>
    </header>
    <content class="content">
      <instructions />
      <pangram />
    </content>
  </main>
</template>

<script>
// import Vue from "vue"
import Instructions from "./components/Instructions.vue"
import Pangram from "./components/Pangram.vue"
import "@fontsource/major-mono-display"

export default {
  name: 'app',
  components: {
    Instructions,
    Pangram
  },
  data () {
    return {
      msg: 'K2 Sports Code Challenge'
    }
  }
}
</script>


<style>

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  color: #323a45;
  font-family: "Open Sans", sans-serif;
}

button {
  cursor: pointer;
  padding: 1em;
}

button:disabled:hover {
  cursor: not-allowed;
}

.content {
  display: flex;
  padding: 1em;
  width: 100vw;
}

.header {
  display: flex;
  background-color: #323a45;
  height: 15vh;
  padding-left: 1em;
}

h1 {
  align-self: center;
  color: #fff;
  font-family: "Major Mono Display", monospace;
  font-size: 3em;
}
</style>
