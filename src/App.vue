<template>
  <div id="app">
<h1>Animals quiz</h1>
<quiz-box> </quiz-box>
  </div>
</template>

<script>
import quizBox from './components/quizBox.vue';

export default {
  name: 'App',
  data(){
    return {
      questions: []
    }
  },
  mounted() {

  fetch('https://opentdb.com/api.php?amount=10&category=27&difficulty=easy&type=boolean')
  .then(res => res.json())
  .then(results => this.questions = results)
},


  components: {
    "quiz-box": quizBox
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
