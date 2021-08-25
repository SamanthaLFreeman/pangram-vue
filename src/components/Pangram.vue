<template>
  <div class="app-form">
    <section class="form">
      <div class="field">
        <div v-if="isSubmitted === false">
          <div class="">
            <label class="label">Pangram</label>
            <input v-model="form.pangram" class="input" type="text" placeholder="Add Sentence here...">
          </div>
        </div>
        <div v-if="isSubmitted === true">
          {{ isPangram(form.pangram) }}
        </div>
      </div>
  
      <button v-on:click="checkSubmit(form.pangram)" type="submit" :disabled="!form.pangram">
        <span>{{this.buttonLabel()}}</span> 
      </button>
    </section>
  </div>
</template>

<script>
// import Vue from "vue";
// import remove from "lodash/remove";

export default {
  name: "pangram",
  data() {
    return {
      isSubmitted: false,
      form : {
        pangram: "",
      }
    } 
  },
  methods: {
    checkSubmit(sentence) {
      if(this.isSubmitted) {
        this.tryAgain();
      } else {
        this.isPangram(sentence);
      }
    },
    isPangram(sentence) {
      let alphabet = 'abcdefghijklmnopqrstuvwxyz'.split('');
      let missingLetters = [];

      alphabet.forEach(letter => {
        let lowerCaseSentence = sentence.toLowerCase();
        if(!lowerCaseSentence.includes(letter)) {
          missingLetters.push(letter);
        }
      })

      this.isSubmitted = true;
      let message = missingLetters.length > 0 ? `Missing Letters: ${missingLetters.join('')}` : 'Pangram!!!';
      return message;
    },
    tryAgain() {
      this.isSubmitted = false;
      this.form.pangram = '';
    },
    buttonLabel() {
      let name = this.isSubmitted === true ? 'TRY AGAIN' : 'SUBMIT';
      return name;
    }
  } 
};

</script>

<style scoped lang="scss">

</style>