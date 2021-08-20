<template>
  <div id="app">
     <img src="">
     <h1>{{ msg }}</h1>
    <pangram></pangram>
  </div>
</template>

<script>
import Vue from "vue"
import Pangram from "./components/Pangram.vue"
export default {
  name: 'app',
  components: {
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
</style>
