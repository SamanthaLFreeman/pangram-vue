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
#app {

}

button:disabled:hover {
  cursor: not-allowed;
}
</style>
