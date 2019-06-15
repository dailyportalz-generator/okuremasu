<template>
  <div id="app">
    <template>
      <span v-if="step < 6"></span>
      <!-- <span v-if="step < 6"><b>step{{step+1}}</b></span> -->
      <SelectQuestion
        key="question1"
        v-if="step === 0"
        v-model="questions.q1"
        @next="handleNext"
        :message="messageList[0]"
        :choices="choicesList[0]"
        :step="step"
      />

      <SelectQuestion
        key="question2"
        v-if="step === 1"
        v-model="questions.q2"
        @next="handleNext"
        :message="messageList[1]"
        :choices="choicesList[1]"
      />

      <SelectQuestion
        key="question3"
        v-if="step === 2"
        v-model="questions.q3"
        @next="handleNext"
        :message="messageList[2]"
        :choices="choicesList[2]"
      />

      <SelectQuestion
        key="question4"
        v-if="step === 3"
        v-model="questions.q4"
        @next="handleNext"
        :message="messageList[3]"
        :choices="choicesList[3]"
      />

      <SelectQuestion
        key="question5"
        v-if="step === 4"
        v-model="questions.q5"
        @next="handleNext"
        :message="messageList[4]"
        :choices="choicesList[4]"
      />

      <SelectQuestion
        key="question6"
        v-if="step === 5"
        v-model="questions.q6"
        @next="handleNext"
        :message="messageList[5]"
        :choices="choicesList[5]"
      />
    </template>

    <OkuremasuResult
      :step="step"
      :questions="questions"
    />
  </div>
</template>

<script>
// import OyasumiHeader from './components/OyasumiHeader.vue'
// import InputQuestion from './components/InputQuestion.vue'
import SelectQuestion from './components/SelectQuestion.vue'
import OkuremasuResult from './components/OkuremasuResult.vue'
import { parse } from 'querystring'

export default {
  // name: 'app',
  data() {
    return {
      step: 0,
      questions: {
        q1: 1,
        q2: 1,
        q3: 1,
        q4: 1,
        q5: 1,
        q6: 1,
      }
    }
  },
  components: {
    // OyasumiHeader,
    // InputQuestion,
    SelectQuestion,
    OkuremasuResult
  },
  mounted() {
    const params = parse(location.search.replace('?', ''))
    const isValid = [ 'q1', 'q2', 'q3', 'q4', 'q5', 'q6'].every((val) => {
      if (!params[val]) {
        return false
      }
      return true
    })
    if (isValid) {
      const questions = {
        // name: params.name,
        // title: parseInt(params.title),
        q1: parseInt(params.q1),
        q2: parseInt(params.q2),
        q3: parseInt(params.q3),
        q4: parseInt(params.q4),
        q5: parseInt(params.q5),
        q6: parseInt(params.q6)
      }
      this.questions = questions
      this.step = 6
    }
  },
  methods: {
    handleNext() {
      this.step ++
    },
    // handleStart(startData) {
    //   this.questions.name = startData.name
    //   this.questions.title = startData.title
    //   this.handleNext()
    // }
  },
  computed: {
    messageList() {
      return [
        'まずとにかく謝ろう',
        '何分遅れる？',
        'いいわけしときましょうか。',
        '話をずらそう',
        'ふたたびお詫びを',
        'しめは？',
      ]
    },
    choicesList() {
      return [
        ['ノーマルに','ビジネスライクに','バカっぽく','謝り倒せ！'],
        ['10分以内','30分ぐらい','1時間ぐらい','わからないぐらい'],
        ['仕事モードで','電車のせいに','正直すぎるぐらいに','大人の理由で'],
        ['やや開きなおって','目をそらせ','すがすがしく','力技で'],
        ['慌てっぷりをアピール','低姿勢に','独り言のように','しっとりと'],
        ['ノーマルに','誠意がある感じで','お金で済ます','ネコ好きなあの人に']
      ]
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

#app {
  font-family: sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  max-width: 540px;
  font-size: 12px;
  /* font-weight: bold; */
  /* padding: 0 50px; */
}
</style>