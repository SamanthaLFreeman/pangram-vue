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
      aria-label="response message" 
      :class=" isCorrect ? 'success' : 'error'"
      class="pangram-resp pangram-container" 
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

export default {
  name: "pangram",
  data() {
    return {
      isCorrect: true,
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
      let alphabet = "abcdefghijklmnopqrstuvwxyz".split("");
      let missingLetters = [];

      alphabet.forEach(letter => {
        let lowerCaseSentence = sentence.toLowerCase();
        if(!lowerCaseSentence.includes(letter)) {
          missingLetters.push(letter);
        }
      })

      this.isSubmitted = true;
      let message = missingLetters.length > 0 ? `Missing Letters: ${missingLetters.join("")}` : "Pangram!";
      this.isCorrect = message.includes("Pangram!");
      return message;
    },
    tryAgain() {
      this.isSubmitted = false;
      this.form.pangram = "";
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
  color: #ff0033;
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

.success {
  font-family: "Major Mono Display", monospace;
  font-size: 3em;
}

.pangram-resp {
  height: 15vh;
  text-align: center;
}
</style>