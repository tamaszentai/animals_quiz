<template lang="html">
  <div>


    <h3>{{ currentQuestion.question }}</h3>
    <ul>
      <li v-for="(answer,index) in answers "
      @click="selectAnswer(index)"
      :class="[selectedIndex === index ? 'selected' : '']">
        {{ answer }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'quiz-box',
  props: {
    currentQuestion: Object
  },
  data(){
    return {
      selectedIndex: null
    }
  },
  computed: {
    answers() {
      let answers = [... this.currentQuestion.incorrect_answers]
      answers.push(this.currentQuestion.correct_answer)
      return answers
    }
  },
  methods: {
    selectAnswer(index){
      this.selectedIndex = index
      console.log(index)
    }
  }
}
</script>

<style lang="css" scoped>

ul {
}

li {
  list-style-type: none;
  padding: 10px;
  cursor: pointer;
}

li:hover {
  background-color: yellow;
}

.selected {
  background-color: dodgerblue;
}


</style>
