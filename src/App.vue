<template>
  <div id="app">
    <h1>Animals Quiz</h1>
    <quiz-box
      v-if="questions.length"
     :currentQuestion="questions[index]" />
     <button>Submit</button>
     <button @click="nextQuestion">Next</button>
  </div>
</template>

<script>
import QuizBox from './components/QuizBox.vue';

export default {
  name: 'App',
  data(){
    return {
      questions: [],
      index: 0
    }
  },

  mounted() {
    fetch('https://opentdb.com/api.php?amount=10&category=27&type=multiple')
    .then(res => res.json())
    .then(res => this.questions = res.results)
  },


  components: {
    "quiz-box": QuizBox
  },
  methods: {
    nextQuestion(){
      this.index++
    }
  }
}
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
