<template>
  <main id="app">
    <header>
      <h1>{{ msg }}</h1>
    </header>
    <instructions />
    <pangram />
  </main>
</template>

<script>
// import Vue from "vue"
import Instructions from "./components/Instructions.vue"
import Pangram from "./components/Pangram.vue"
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
  font-family: "Open Sans", sans-serif;
}

button {
  border: none;
  cursor: pointer;
  padding: 1em;
}

button:disabled:hover {
  cursor: not-allowed;
}
</style>
