<!-- src/components/SelectQuestion.vue -->
<template>
  <form @submit.prevent="handleSubmit" class="select-question">
    <dl>
      <dt>
        <span v-if="step < 6"><b>step{{step+1}}</b></span>
        {{message}}
      </dt>
      <dd>
        <template v-for="(choice, i) in choices">
          <div>
            <label :key="choice" for="">
              <input type="radio" v-model="selectedValue" :value="i+1" >
              <span>{{choice}}</span>
            </label>

          </div>
        </template>
      </dd>
    </dl>
    <button>次へ</button>
  </form>
</template>

<script>
export default {
  props: {
    message: String,
    choices: Array,
    value: Number,
    step: Number,
  },
  data() {
    return {
      selectedValue: this.value
    }
  },
  methods: {
    handleSubmit() {
      this.$emit('input', this.selectedValue)
      this.$emit('next')
    }
  }
}
</script>

<style scoped>
.select-question {
  margin-bottom: 1em;
  /* padding-bottom: 24px; */
  /* border-bottom: dotted 1px #c6c6c6; */
}

h3 {
  font-size: 1em;
}


dd {
  margin: 16px 0 0;
  /* padding: 0 0 8px 0; */
}
dd > div {
  margin-bottom: 8px;
}
dd > div input {
  margin-right: 8px;
}
button {
  /* width: 120px; */
}

input[type='text'] {
  margin-right: 20px;
}
</style>