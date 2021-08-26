<template>
  <section class="instructions">
    <p class="instruction">Pangrams are sentences which use every single letter of the alphabet. ex: “A quick brown fox jumps over the lazy dog.”</p>
    <p class="instruction">Please fork this project and write a function which determines if the input is a pangram or not. If the input is a pangram return "Pangram!" If it is not, 
    please return the letters of the alphabet that are missing from the sentance. The sentence may include upper or lowercase letters or special characters
    but the returned letters should all be lowercase with special characters ommitted. You may use any libraries or tools at your disposal to help complete this project.
    Please also include responsive css styles on this page (this paragraph included) and the output as well, the design is up to you (be creative if you like!). Bonus points for validation and including accessibility.</p>

    <p class="instruction"> Vue.js documentation can be found here: <a href="https://vuejs.org/">Vue documentation</a>
    </p>
  </section>
</template>

<script>

export default {
  name: "instructions"
};

</script>

<style scoped lang="scss">
.instructions {
  width: 50%;
}

.instruction {
  font-size: 1.4em;
  padding: 1em;
}
</style>