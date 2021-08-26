<template>
  <section class="pangram">
    <form v-if="isSubmitted === false">
      <label class="label">Pangram</label>
      <input 
        aria-label="sentence input"
        v-model="form.pangram" 
        class="input" 
        type="text" 
        placeholder="Add Sentence here..." >
    </form>
    <div aria-label="response message" v-if="isSubmitted === true">
      {{ isPangram(form.pangram) }}
    </div>

    <button 
      :aria-label="buttonLabel().toLowerCase()"
      v-on:click="checkSubmit(form.pangram)" 
      type="submit" 
      :disabled="!form.pangram" >
      <span>{{ buttonLabel() }}</span> 
    </button>
  </section>
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