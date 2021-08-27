<template>
  <section class="pangram">
    <form class="pangram-form" v-if="isSubmitted === false">
      <label class="pangram-label pangram-container">Enter Pangram:</label>
      <textarea 
        aria-label="sentence input"
        v-model="form.pangram" 
        class="pangram-input pangram-container" 
        type="text" 
        rows="3"
        placeholder="Add Sentence here..." />
    </form>
    <div 
      :class=" isSubmitted ? 'error' : 'success'"
      class="pangram-resp pangram-container" 
      aria-label="response message" 
      v-if="isSubmitted === true" >
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
import $ from "jquery";

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
      $(".pangram-resp").css("color", "red");
      if(this.isSubmitted) {
        this.tryAgain();
      } else {
        this.isPangram(sentence);
      }
    },
    isPangram(sentence) {
      let alphabet = "abcdefghijklmnopqrstuvwxyz".split("");
      let missingLetters = [];

      alphabet.forEach(letter => {
        let lowerCaseSentence = sentence.toLowerCase();
        if(!lowerCaseSentence.includes(letter)) {
          missingLetters.push(letter);
        }
      })

      this.isSubmitted = true;
      let message = missingLetters.length > 0 ? `Missing Letters: ${missingLetters.join("")}` : "Pangram!!!";
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
.error {
  color: red;
}

.pangram {
  display: flex;
  flex-direction: column;
  font-size: 1.2em;
  padding: 3em;
  width: 50vw;
}

.pangram-container {
  margin: 0 0 10px 0;
}

.pangram-form {
  display: flex;
  flex-direction: column;
}

.pangram-input {
  font-size: 1.2em;
  padding: .5em;
}

.pangram-label { 
  font-weight: bold;
}

// .pangram-resp {
//   color: #000;
// }
</style>